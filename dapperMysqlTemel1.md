## Dapper ile Mysql İşlemleri ##

### Dapper Nedir? ###
>Dapper, .NET uygulamalarında veritabanı ile bağlantı kurarak tablolar üzerinde kolay ve hızlı bir şekilde ekleme silme, güncelleme ve arama yapabilmemize yarayan bir kütüphanedir.  ADO.NET kadar hızlı çalışmaktadır. Dapper ile ilgili daha fazla bilgi almak için https://dapper-tutorial.net/dapper sitesinden faydalanabilirsiniz.

### ORM (Object Relational Mapping) nedir? ###
>Bir ORM, veritabanı ve programlama dili arasında eşleme yapmaktan sorumlu olan bir Nesne İlişkisel Eşleştiricisidir. Yani veritabanından bulunan tablolar ile c# tarafında oluşturulan sınıfların birbiriyle eşleştirilmesini sağlayarak kod yazımını ve okunurluğunu kolaylaştırmaktadır. Dapper ORM'yi desteklediği ve basit olduğundan dolayı  bir Mikro ORM kategorisine girmektedir. Hatta ulaştığı hızlardan dolayı "King of Micro ORM " yani Mikro ORM'lerin kralı olarak adlandırılır.

**CRUD:**  Create - Read - Update - Delete kelimelerinin baş harflerinden oluşur.  Yani Ekleme, Okuma, Güncelleme, silme işlemlerini belirtmek İçin CRUD kısaltması kullanılır

### Dapper Nasıl çalışır? ###
1.  IDbConnection nesnesi oluşturularak veritabanına bağlantı kurulur.
2.  CRUD işlemleri için sorgu yazılır.
3.  Execute metodu ile yazılan sorgular çalıştırılır

### Kullanılacak Olan Veritabanı sql kodları ve workbench'deki tasarım  penceresi ###

```sql
CREATE TABLE `eokul`.`tblnot` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `ogrenciAdSoyad` VARCHAR(45) NOT NULL,
  `puan1` TINYINT(3) NOT NULL,
  `puan2` TINYINT(3) NOT NULL,
  `ortalama` DOUBLE NOT NULL,
  PRIMARY KEY (`id`));
```

![image](https://user-images.githubusercontent.com/28144917/166909704-b41ab263-4a34-4110-860d-a1694173e9ef.png)

**Örnek-1**
> Aşağıdaki örnekte mysql ile bağlantı kuralarak eokul veritabanındaki tbnot tablosundaki tüm veriler ekrana getirilmektedir.

```csharp
using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "select * from tblnot";

               var ogrenciler= baglanti.Query<OgrenciPuan>(sorgu).ToList();
                
                ogrenciler.ForEach(x => Console.WriteLine(x)); //Tüm Öğrencileri ekrana console ekranına yazdırır.

                dgOgrenci.ItemsSource=ogrenciler;     // Tüm öğrencileri datagrid içerisinde görüntüler.
            }
```


### Kullanılacak olan OgrenciPuan Sınıfı ###

```csharp
 class OgrenciPuan
    {
        public int id { get; set; }
        public string ogrenciAdSoyad { get; set; }

        public int puan1 { get; set; }
        public int puan2 { get; set; }
        public double ortalama { get; set; }
        public override string ToString()
        {
            return $"{id}-{ogrenciAdSoyad}-{puan1}-{puan2}-{ortalama}";
        }
    }
    
```

### Dapper'da sık kullanılan metodlar  ###
> Dapperda sık kullanılan metotlar aşağıda bulunmaktadır. Daha fazla bilgi almak  https://dapper-tutorial.net/dapper linki ile dapper resmi sitesinden faydalanabilirsiniz.

#### 1. Execute ####
> Execute metodu bir komutu yada sql sorgusunu bir veya birden fazla çalıştırmak için kullanılır. Çalıştıldıktan sonra etkilenen kayıt sayısını sonuç olarak döndürür. Genellikle **INSERT-UPDATE-DELETE** sorguları ile kullanılır.

**Örnek-1 - Ekleme Sorgusu**
```csharp
 using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
              OgrenciPuan yeniogrenci = new OgrenciPuan
                {
                    ogrenciAdSoyad = "Serkan TAN",
                    puan1 = 95,
                    puan2 = 85,
                    ortalama = 90
                };

                string sorgu = "Insert into tblnot(ogrenciAdSoyad,puan1,puan2,ortalama) values (@ogrenciAdSoyad,@puan1,@puan2,@ortalama)";

                int etkilenenKayitSayisi= baglanti.Execute(sorgu, yeniogrenci);
     }           
```

**Örnek-2 Güncelleme Sorgusu**
```csharp
            using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "UPDATE tblnot set ogrenciAdSoyad=@ogrenciAdSoyad WHERE id=@id";
                int guncellenenKayıtSayisi=baglanti.Execute(sorgu,new { ogrenciAdSoyad ="EKİN SOLMAZ", id=4});
                MessageBox.Show($"{guncellenenKayıtSayisi} tane kayıt güncellenmiştir.");
            }
                
```
**Örnek-3 Silme Sorgusu**
```csharp
    
            using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "DELETE FROM tblnot WHERE id=@id";
                int silinenKayıtSayisi = baglanti.Execute(sorgu, new { id = 2 });
                MessageBox.Show($"{silinenKayıtSayisi} tane kayıt silinmiştir.");
            }          
                
```

#### 2. Query #### 

> Query metodu parametre olarak verilen sql sorgusunu çalıştırır ve sonucu liste olarak döndürür. Sonucu döndürürken arka planda sonuca karşılık gelen nesneye eşleştirme işlemi de yapar. 

**Örnek**
> Aşağıdaki örnekte tbnot tablosundaki tüm kayıtları seçen  "select * from tblnot" sorgusu çalıştırılmıştır. Sonucunda gelen veriler bir OgrenciPuan listesine eşleştirilerek döndürülmüştür.

```csharp
              string sorgu = "select * from tblnot";
              var ogrenciler= baglanti.Query<OgrenciPuan>(sorgu).ToList();
```

#### 3. QueryFirst  ####
> QueryFirst metodu parametre olarak verilen sql sorgusunu çalıştırır ve sonuca uygun kayıtlardan sadece ilkini döndürür. Sonucu döndürürken arka planda sonuca karşılık gelen nesneye eşleştirme işlemi de yapar. 

**Not:** QueryFirst metodu sorguyu çalıştırdığında eğer sorguya uygun bir kayıt yoksa QueryFirst metodu hata fırlatır. Hata yerine varsayılan değer döndürülmesi istenirse QueryFirstOrDefault metodu kullanılır.

**Örnek-1**
> Aşağıdaki örnekte tbnot tablosundaki tüm kayıtları seçen  "select * from tblnot" sorgusu çalıştırılmıştır.QueryFirst metodu ile  sorguya uygun ilk kayıt ilkogrenci  nesnesine atanmıştır.

```csharp

            using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "select * from tblnot";

                OgrenciPuan ilkogrenci = baglanti.QueryFirst<OgrenciPuan>(sorgu);
                MessageBox.Show(ilkogrenci.ToString());
            }
      
```

**Örnek-2**
> Aşağıdaki Örnek id=2 olan öğrenciyi bulunanOgrenci referansına atar.

```csharp
            using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "select * from tblnot where id=@id";
                OgrenciPuan bulunanOgrenci = baglanti.QueryFirst<OgrenciPuan>(sorgu,new {id=2});
                MessageBox.Show(ilkogrenci.ToString());
            }
           
      
```
 

#### 4. QueryFirstOrDefault ####
> QueryFirstOrDefault metodu parametre olarak verilen sql sorgusunu çalıştırır ve sonuca uygun kayıtlardan sadece ilkini döndürür. Eğer döndürecek kayıt yoksa hata fırlatmaz varsayılan değer döndürür. 


> Aşağıdaki örnekte tbnot tablosundaki tüm kayıtları seçen  "select * from tblnot" sorgusu çalıştırılmıştır.QueryFirst metodu ile  sorguya uygun ilk kayıt ilkogrenci  nesnesine atanmıştır.

```csharp

            using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "select * from tblnot where id=@id";

                OgrenciPuan bulunanOgrenci = baglanti.QueryFirstOrDefault<OgrenciPuan>(sorgu,new {id=6});
                if (bulunanOgrenci != null)
                {
                    MessageBox.Show(bulunanOgrenci.ToString());
                }
                else
                {
                    MessageBox.Show("6 nolu id ye ait ogrenci bulunamadı");
                }
               
            }
      
```

#### 5. QuerySingle ####
> QuerySingle metodu parametre olarak verilen sql sorgusunu çalıştırır.Sorguya uygun tek bir kayıt varsa döndürür.Sorgu sonucunda birden fazla kayıt varsa veya sorguya uygun hiç bir kayıt yoksa hata fırlatır.

#### 6. QuerySingleOrDefault ####

> QuerySingleOrDefault metodu parametre olarak verilen sql sorgusunu çalıştırır.Sorguya uygun tek bir kayıt varsa döndürür. Sorgu sonucunda birden fazla kayıt varsa veya sorguya uygun hiç bir kayıt yoksa varsayılan değer döndürür.


### Root kullanıcısının Kimlik Doğrulama tipini  (authentication type) standart olarak ayarlamak ###

```shell
cd "C:\Program Files\MySQL\MySQL Server 8.0\bin"

C:\Program Files\MySQL\MySQL Server 8.0\bin> mysql -u root -p
Enter password: *********

mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'yeni Şifre';
```


### Veritabınından Verileri Çekip DataGrid içerisinde görüntüleme ###

```csharp
 string ConnectionString = "host=localhost;port=3306;user id=root;password=mtal2022;database=eokul;SslMode=None";
 
 private void BtnListele_Click(object sender, RoutedEventArgs e)
        {
            using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "select * from tblnot";

                var ogrenciler= baglanti.Query<OgrenciPuan>(sorgu).ToList();

                ogrenciler.ForEach(x => Console.WriteLine(x));

                dgOgrenci.ItemsSource=ogrenciler;
            }
        }
 ```
 
 
### Veritabınına Yeni Öğrenci Ekleme ###

```csharp
 string ConnectionString = "host=localhost;port=3306;user id=root;password=mtal2022;database=eokul;SslMode=None";
 
 private void BtnYeniOgrenciEkle_Click(object sender, RoutedEventArgs e)
        {
            using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                 OgrenciPuan yeniogrenci = new OgrenciPuan
                {
                    ogrenciAdSoyad = "Serkan TAN",
                    puan1 = 95,
                    puan2 = 85,
                    ortalama = 90
                };

                string sorgu = "Insert into tblnot(ogrenciAdSoyad,puan1,puan2,ortalama) values (@ogrenciAdSoyad,@puan1,@puan2,@ortalama)";

                int etkilenenKayitSayisi= baglanti.Execute(sorgu, yeniogrenci);
                MessageBox.Show(etkilenenKayitSayisi.ToString());

            }
        }
 ```
