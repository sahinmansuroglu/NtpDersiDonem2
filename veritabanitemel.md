## Veritabanı Temelleri, MYSQL, SQL(Sorgulama Dili) ##

> Veritabanı Temelleri, MYSQL ve  SQL(Sorgulama Dili) için aşağıda linki verilen Ders Kitabının 195. - 246. Sayfaları arası takip edilecektir.

 [Ders Kitabını İndirmek için Tıklayınız](http://meslek.eba.gov.tr/upload/dk10/Nesne_Tabanli_Programlama_10_3.pdf)
 
 ### Veritabanı Oluşturma ###
 
 > Aşağıdaki SQL kodu muhasebe adında bir veritabanı oluşturur
 ```sql
 create database muhasebe
 ```
 
 
### Primary Key Örnek ###

![image](https://user-images.githubusercontent.com/28144917/165025003-c2c26e07-313c-48d9-94c5-2b962bfd23fc.png)

 
### Unique Key Örnek ###

![image](https://user-images.githubusercontent.com/28144917/165025025-a79c465d-971e-4133-8d22-8cafa711458c.png)

### Foreign Key Örnek ###

![image](https://user-images.githubusercontent.com/28144917/165025119-3ffd2d5e-963c-4222-ad8d-bbc1da7e15e6.png)


### Tablo Oluşturma (SQL ile) ###

#### Örnek-1 ####
> Aşağıdaki örnek eokul veritabanın içerisinde tblKisi adında bir tablo oluşturur. Bu tablonun içerisinde sn, adsoyad ve yas sutunları bulunur. sn  primary key ve not null olarak belirlenmiştir.

 ```sql
CREATE TABLE `eokul`.`tblkisi` (
  `sn` INT NOT NULL,
  `adsoyad` VARCHAR(45) NULL,
  `yas` SMALLINT not NULL,
  PRIMARY KEY (`sn`));
 ```
 
 #### Örnek-2 ####
 > Aşağıdaki Örneğin yukarıdan farkı sn auto_ıncrement iel otomatik 1 arttırılmıştır.
 
  ```sql
CREATE TABLE `eokul`.`tblkisi` (
  `sn` INT NOT NULL AUTO_INCREMENT,
  `adSoyad` VARCHAR(45) NOT NULL,
  `yas` TINYINT NOT NULL,
  PRIMARY KEY (`sn`)
  );
 ```
 
 
### Tablo Oluşturma (Tasarım Ekranında) ###

![image](https://user-images.githubusercontent.com/28144917/165025400-14327818-8cf5-4393-8354-edb6ece469d9.png)

![image](https://user-images.githubusercontent.com/28144917/165025405-7cef5a42-33df-4341-b598-8fdfb79a07f0.png)

### İlişkili tablo Örneği

![image](https://user-images.githubusercontent.com/28144917/165026934-0b7a46cd-6854-4d94-9114-7ac48d89eb99.png)

#### Kullanılan Tablolar

```sql
CREATE TABLE `dersler` (
  `derskodu` varchar(4) NOT NULL,
  `dersadi` varchar(45) DEFAULT NULL,
  `dersSaati` tinyint DEFAULT NULL,
  PRIMARY KEY (`derskodu`)
)

CREATE TABLE `ogrencibilgi` (
  `ogrenciNo` int NOT NULL,
  `ogrenciAdi` varchar(20) NOT NULL,
  `ogrenciSoyadi` varchar(20) NOT NULL,
  `ogrenciBolumu` varchar(30) NOT NULL,
  `ogrencisinifi` int NOT NULL,
  `ogrenciDogumTarihi` date NOT NULL,
  PRIMARY KEY (`ogrenciNo`)
)
  CREATE TABLE `ogrencinot` (
  `idogrencinot` int NOT NULL,
  `ogrNoFK` int NOT NULL,
  `dersKoduFK` varchar(4) NOT NULL,
  `yazili1` tinyint NOT NULL,
  `yazili2` tinyint NOT NULL,
  `yazili3` tinyint NOT NULL,
  `uygulama1` tinyint NOT NULL,
  `uygulama2` tinyint NOT NULL,
  `sozlu1` tinyint NOT NULL,
  `sozlu2` tinyint NOT NULL,
  `ortalama` float DEFAULT '0',
  PRIMARY KEY (`idogrencinot`)
)

CREATE TABLE `tblmezuniyet` (
  `idtblMezuniyet` int NOT NULL,
  `ogrenciNoFK` int NOT NULL,
  `mezunYili` int NOT NULL,
  `mezunOrtalamasi` float NOT NULL,
  PRIMARY KEY (`idtblMezuniyet`)
) 
```

### Tabloların MYSQL Workbench ile tasarımı ###
![dersler](https://user-images.githubusercontent.com/28144917/165704848-cd323104-8647-4b09-a8a1-165b8628991b.JPG)
![ogrenciBilgi](https://user-images.githubusercontent.com/28144917/165704853-08caaee7-0e69-4b58-9fbf-a9565eae32db.JPG)
![ogrNot](https://user-images.githubusercontent.com/28144917/165704856-215beddc-53a5-405c-84fa-13eff445f9a3.JPG)
![tblmezuniyet](https://user-images.githubusercontent.com/28144917/165704857-d9eba488-8a6c-4545-bb64-d653e76b5db3.JPG)
