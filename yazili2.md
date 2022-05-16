### Kullanılacak olan Class'lar ### 

```csharp
public class Ders
    {
        public string DersKodu { get; set; }
        public string DersAdi { get; set; }
        public int DersSaati { get; set; }
    }
  public class Ogrenci
    {
        public int id { get; set; }
        public string Ad { get; set; }
        public int OkulNo { get; set; }
        public string Soyad { get; set; }
          public override string ToString()
        {
            return $"{OkulNo} : {Ad} {Soyad} ";
        }
    }   
    public class OgrenciPuan
    {
        public int id { get; set; }
         public int OgrenciId { get; set; }
        public string DersKodu { get; set; }
        public int Yazili1 { get; set; }
        public int Yazili2 { get; set; }
        public int Performans1 { get; set; }
        public int Performans2 { get; set; }
        public double Ortalama { get; set; }
        public string Durum { get; set; }
      
    }
    
     class OgrenciPuanModel:OgrenciPuan{

          
            public String DersAdi { get; set; }
            public String DersSaati { get; set; }
            public String Ad { get; set; }
            public String Soyad { get; set; }
            

        public override string ToString()
            {
                return $"{Ad} {DersAdi} {Performans1}";

            }

        }
    
```

Tablonun SQL Kodları

[sqlsınav.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8679418/sqlsinav.zip)

```sql
CREATE TABLE `ders` (
  `DersKodu` varchar(5) NOT NULL,
  `DersAdi` varchar(45) NOT NULL,
  `DersSaati` int NOT NULL,
  PRIMARY KEY (`DersKodu`)
)

CREATE TABLE `ogrenci` (
  `Id` int NOT NULL AUTO_INCREMENT,
  `Ad` varchar(45) NOT NULL,
  `Soyad` varchar(45) NOT NULL,
  `OkulNo` int NOT NULL,
  PRIMARY KEY (`Id`),
  UNIQUE KEY `OkulNo_UNIQUE` (`OkulNo`)
)

CREATE TABLE `ogrencipuan` (
  `Id` int NOT NULL AUTO_INCREMENT,
  `OgrenciId` int NOT NULL,
  `DersKodu`  varchar(5) NOT NULL,
  `Yazili1` int DEFAULT NULL,
  `Yazili2` int DEFAULT NULL,
  `Performans1` int DEFAULT NULL,
  `Performans2` int DEFAULT NULL,
  `Ortalama` double DEFAULT NULL,
  `Durum` varchar(5) DEFAULT NULL,
  PRIMARY KEY (`Id`)
)
```


### Tabloları Birleştirme ###

```sql
select ders.DersAdi, ogrencipuan.Performans1,ogrenci.Ad
from ogrencipuan
inner  join ders
on ders.DersKodu=ogrencipuan.DersKodu
inner  join ogrenci
on ogrenci.Id=ogrencipuan.OgrenciId
```


```sql
select ders.*, ogrencipuan.*,ogrenci.* from ogrencipuan  
inner  join ders on ders.DersKodu = ogrencipuan.DersKodu 
inner join ogrenci on ogrenci.Id = ogrencipuan.OgrenciId
                               
```
### Proje Dosyası ###

[VeritabaniProjesi1.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8679437/VeritabaniProjesi.zip)
[VeritabaniProjesieski.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8695587/VeritabaniProjesi.zip)
[VeritabaniProjesi En Eski.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8698112/VeritabaniProjesi.zip)

