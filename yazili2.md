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
        public Ogrenci Ogrenci { get; set; }
        public Ders Ders { get; set; }
        public int Yazili1 { get; set; }
        public int Yazili2 { get; set; }
        public int Performans1 { get; set; }
        public int Performans2 { get; set; }
        public double Ortalama { get; set; }
        public string Durum { get; set; }

        
    }
    
```

Tablonun SQL Kodları
[SınavSQL.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8678782/SinavSQL.zip)

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
  `DersId` varchar(5) NOT NULL,
  `Yazili1` int DEFAULT NULL,
  `Yazili2` int DEFAULT NULL,
  `Performans1` int DEFAULT NULL,
  `Performans2` int DEFAULT NULL,
  `Ortalama` double DEFAULT NULL,
  `Durum` varchar(5) DEFAULT NULL,
  PRIMARY KEY (`Id`)
)
```
