## SQl Sorguları ile ekleme silme Listeleme Güncelleme İşlemleri ##
Sorgulamada Kullanılan 

### Insert into Ekleme (bilgi Girişi) ### 

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
 
### Select Deyimi ###


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
