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

### Dapper'da sık kullanılan metodlar  ###
> Dapperda sık kullanılan metotlar aşağıda bulunmaktadır. Fazlası için https://dapper-tutorial.net/dapper linki ile dapper resmi sitesinden faydalanabilirsiniz.
#### 1. Execute ####
> Execute metodu bir komutu yada sql sorgusunu bir veya birden fazla çalıştırmak için kullanılır. Çalıştıldıktan sonra etkilenen kayıt sayısını sonuç olarak döndürür. Genellikle **INSERT-UPDATE-DELETE** sorguları ile kullanılır.

#### 2. Query #### 
#### 3. QueryFirst  ####
#### 4. QueryFirstOrDefault ####
#### 5. QuerySingle ####
#### 6. QuerySingleOrDefault ####




### Root kullanıcısının Kimlik Doğrulama tipini  (authentication type) standart olarak ayarlamak ###
```
cd "C:\Program Files\MySQL\MySQL Server 8.0\bin"

C:\Program Files\MySQL\MySQL Server 8.0\bin> mysql -u root -p
Enter password: *********

mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'yeni Şifre';

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
                OgrenciPuan ogrenciPuan=new OgrenciPuan{ 
                    ogrenciAdSoyad="AYla OZAN",
                    puan1=57,
                    puan2=45,
                    ortalama=51
                };  
                string eklemeSorgusu= "Insert into tblnot(ogrenciAdSoyad,puan1,puan2,ortalama)  values (@ogrenciAdSoyad,@puan1,@puan2,@ortalama)";
                baglanti.Execute(eklemeSorgusu,ogrenciPuan);

            }
        }
 ```
