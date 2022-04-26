## SQl Sorguları ile ekleme silme Listeleme Güncelleme İşlemleri ##
Sorgulamada Kullanılan 

### Insert into komutu (bilgi Girişi) ### 

> Temel Kullanım

```sql
insert into tabloadı (alan1, alan2, …, alan(n)) VALUES (deger1, deger2, …, deger(n))
```

> Örnek

```sql
 
 insert into eokul.dersler (derskodu, dersadi) values ("PRT","Programlama temelleri")
 insert into eokul.dersler values ("RES","Resim")
 insert into ogrencinot (ogrNoFK,dersKoduFK) values (4014,"RES")
 
 ```
 
### Select Komutu ###


> Temel Kullanım

```sql
SELECT {*, SÜTUN, …} FROM tabloAdı
```


Örnek

```sql
SELECT * FROM ogrencibilgi;
SELECT ogrenciNo,ogrenciAdi,ogrenciSoyadi FROM ogrencibilgi;
SELECT * FROM ogrencibilgi where ogrenciAdi="furkan" ;
SELECT * FROM ogrencibilgi where ogrenciAdi="furkan" AND ogrenciSoyadi="COŞKUN"  ;
SELECT * FROM ogrencibilgi where ogrenciNo between  4015 and 4050
SELECT * FROM ogrencibilgi order by ogrenciAdi asc
SELECT * FROM ogrencibilgi order by ogrencisinifi DESC
SELECT * FROM ogrencibilgi WHERE ogrenciBolumu="ELEKTRİK" OR ogrencisinifi>10
SELECT * FROM ogrencibilgi WHERE ogrenciBolumu="ELEKTRİK" AND ogrencisinifi>10
```

### Update Komutu (Güncelleme) ###

> Temel Kullanım

```sql
UPDATE tablo SET sütun1=değer1, sütun2=değer2,…WHERE şart
```


Kullanılan Tablo

![image](https://user-images.githubusercontent.com/28144917/165227623-883c19e2-c693-46a9-ac38-1591d7c9ee9d.png)

![image](https://user-images.githubusercontent.com/28144917/165228726-cbf0c1dd-adf3-42d6-ab55-f1ac35c44673.png)
```sql
update tblpuan set ortalama=(puan1+puan2)/2 
```
![image](https://user-images.githubusercontent.com/28144917/165228683-08112047-ef57-4831-a9e2-748e06feff02.png)
```sql
update tblpuan set adsoyad="Veli" where id=4; 
```


### Delete Komutu (Kayıt Silme) ###


> Temel Kullanım

```sql
DELETE FROM tablo WHERE şart
```

```sql
DELETE FROM ogrenci WHERE eposta IS NULL
delete from tblpuan where id=3
delete from tblpuan where ortalama<50
delete from tblpuan 
```


### Create ###
> Veri tabanı ya da tablo oluşturmak için kullanılır.

```sql

 CREATE DATABASE eokul
 CREATE TABLE ogrencibilgi


```

**Örnek**
> Aşağıdaki SQL kodu okulotomasyon adında bir veritabanı oluşturur. bu veritabanını kullanarak içinde dersler adında bir tablo oluşturur.
```sql
create database okulotomasyon;
use okulotomasyon;
CREATE TABLE dersler (
  `derskodu` VARCHAR(4) NOT NULL,
  `dersadi` VARCHAR(45) NULL,
  PRIMARY KEY (`derskodu`)
  );
  
  ```
  
### Alter ###
> Var olan bir nesne üzerinde değişiklikler yapmak için kullanılır. Veri alanı eklemek için aşağıdaki kod 
kullanılabilir


```sql
ALTER TABLE personel ADD eposta VARCHAR(40) NULL
```
```sql
use eokul;
ALTER TABLE tblpuan ADD eposta VARCHAR(40) NULL;
```

### Drop ###

Veri tabanındaki herhangi bir nesneyi (tablo veya veri tabanı) kaldırmak için kullanılır. DROP kullanırken 
çok dikkatli olunmalıdır.

```sql
DROP TABLE dersler
drop database eokul3;
```
