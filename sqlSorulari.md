## SQL Soruları ##

![image](https://user-images.githubusercontent.com/28144917/165273746-dff53195-7400-4e1d-8307-c299e15cd0ab.png)

S.1.tblNot tablosundaki tüm kayıtları listeleyen SQL sorguyu yazınız.
……………………………………………………………………………………………………………………………………………………………………………………………………………….

S.2. tblNot tablosundaki ogrAdSoyad ve not1  alanlarını  listeleyen SQL sorguyu yazınız.
……………………………………………………………………………………………………………………………………………………………………………………………………………….

S.3. tblNot tablosundaki tüm alanları ve 2 yazılının ortalamasını (Ortalama isminde yeni bir alanda) listeleyen SQL sorguyu yazınız.
……………………………………………………………………………………………………………………………………………………………………………………………………………….

S.4. tblNot tablosunda not1 değeri 80 ile 100 arasında olan kayıtları listeleten SQL sorguyu yazınız.
……………………………………………………………………………………………………………………………………………………………………………………………………………….

S.5. tblNot tablosununun [ogrAdSoyad], [ders],[not1], [not2]   alanlarına sırasıyla  [”Ahmet SAKİN”], [2], [90, [60] değerlerine sahip  yeni bir kayıt ekleyen SQL sorgusunu yazınız.
…………………………………………………………………………………………………………………………………………………………………………………………………………….

S.6. tblNot tablosununun sn değeri 3 olan kaydın ogrAdSoyad değerini “Mehmet CAN” olarak güncelleyen SQL sorgusunu yazınız.
……………………………………………………………………………………………………………………………………………………………………………………………………………….

S.7. tblNot tablosuna tipi float olan ortalama isminde yeni bir alan ekleyen SQL sorgusunu yazınız
……………………………………………………………………………………………………………………………………………………………………………………………………………….

S.8. tblDers tablosunu silen SQL sorgusunu yazınız.
……………………………………………………………………………………………………………………………………………………………………………………………………………….

S.9. Aşağıdaki sorgular ne iş yapar tek cümleyle yazınız.

a)	SELECT * from tblnot order by ogrAdSoyad desc
……………………………………………………………………………………………………………………………………………..…………………………………………………………….

b)	SELECT sum(dersSaati) as [toplamDersSaati] from tblDers
   ……………………………………………………………………………………………………………………………………………………………..…………………………………………….
   
c)	SELECT avg(not1) as [Ortalama] from tblNot
   ………………………………………………………………………………………………………………………………………………………………………..………………………………….
   
d)	SELECT max(not1)  from tblNot
……………………………………………………………………………………………………………………………………………………………………………..…………………………….

e)	SELECT min(not1)  from tblNot
   …………………………………………………………………………………………………………………………..……………………………………………………………………………….
  
  S.10.tblNot tablosundaki ortalaması 70 dan küçük olan kayıtları aşağıdaki şekilde listeleyen sorguyu yazınız.
  
  ![image](https://user-images.githubusercontent.com/28144917/165274246-dea199ef-edd2-4426-a0a9-b2266263e248.png)
  
  ………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………
  
  ………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………
  
  ………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………………

  S.11. Aşağıdaki tablolarda Birincil anahtar(Primary Key) ve Yabancı Anahtar(Foreign key)alanlarını  gösteriniz (Soldan sağa a, b, c)

![image](https://user-images.githubusercontent.com/28144917/165276509-d54caabd-5244-48bf-b3b0-d99d05d2b473.png)


  ### Cevaplar ###
  
```sql
  
S.1. SELECT * FROM  tblNot

S.2. SELECT ogrAdSoyad,not1  from tblnot

S.3. SELECT ogrAdSoyad,not1, not2 , (not1+not2)/2 as Ortalama from tblnot

S.4. SELECT * from tblnot WHERE not1 between 80 and 100

S.5. INSERT INTO tblNot (ogrAdSoyad, ders,not1, not2) VALUES("Berfin",3,78,99)

S.6. UPDATE tblnot set ogrAdSoyad=" Mehmet CAN " where sn=3

S.7. ALTER TABLE tblNot ADD ortalama float

S.8. drop table tblDers

S.9. 
a)	Tblnot tablosundaki tüm kayıtları ogrAdSoyad alanına göre Z’den A’ya listeler

b)	tblDers tablosundaki dersSaati alanındaki değerlerin toplamını verir.

c)	Tblnot tablosunun not1 alanındaki değerlerin ortalamasını  verir.

d)	Tblnot tablosunun not1 alanındaki değerlerden en büyüğünü verir.

e)	Tblnot tablosunun not1 alanındaki değerlerden en küçüğünü verir.



S.10.     SELECT tblNot.ogrAdSoyad, tblDers.dersAdi, tblNot.not1, tblNot.not2

FROM  tblNot INNER JOIN tblDers ON tblNot.ders=tblDers.sn where  (tblNot.not1+tblNot.not2)/2<70

SELECT tblNot.ogrAdSoyad,
(select [tblDers.dersAdi] from tblDers where tblDers.sn=tblNot.ders) as DersAdi
 FROM tblNot;

```
S.11. 

![image](https://user-images.githubusercontent.com/28144917/165276696-8a3abedd-2157-43d2-a2d4-89467a156aa4.png)


[Word Dosyası Halinde indirmek için Tıklayınız.](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8562020/SQLsORU.docx)
