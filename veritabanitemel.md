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
