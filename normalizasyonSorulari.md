## Normalizasyon Sorusu-1 ##

[Normalizasyon Sorusu-1'i word Dosyası olarak indirmek için tıklayınız](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8562070/normalizasyon1.docx)

![image](https://user-images.githubusercontent.com/28144917/165275247-70e0b2dc-326e-4f16-b726-2f59af5469b7.png)


> Yukarıda yer alan tablo, bir dağıtım firmasına ait veritabanıdır. Bu tablodan yola çıkarak, tabloyu sırası ile Normal Formlara uygun hale getiriniz.
> 
## Normalizasyon Sorusu-1 Cevap ##

**1NF**

>Yapacağımız işlem, aynı hücre içinde yer alan birden fazla veri varsa, bunları satırlar halinde ayrı kayıtlara bölmek. Bu durumda ihtiyaç duyduğumuz tablonun yapısını çiziniz.

![image](https://user-images.githubusercontent.com/28144917/165275476-6d33a60c-863a-4137-899e-ea366e8bfe22.png)

**2NF**

> Yapacağımız işlem, Birincil anahtar yoksa eklemek, varsa tekrarına neden olan sütunları ayırmak. Yukarıdaki tabloda birincil anahtar olarak kullanabileceğimiz Müşteri No alanı var.  aynı hücre içinde yer alan birden fazla veri varsa, bunları satırlar halinde ayrı kayıtlara bölmek. Bu durumda ihtiyaç duyduğumuz tablonun yapısını çiziniz.

![image](https://user-images.githubusercontent.com/28144917/166872494-0452128b-6cab-463c-866f-34b04d2363f5.png)

**3NF**

>2NF olarak ayırdığımız tablolarda, birbirine bağımlı olan sütunları bulup bunları ayrı bir tabloya aktarmamız gerekli.

![image](https://user-images.githubusercontent.com/28144917/166872599-2aad2412-2e21-4357-80aa-0537838f8526.png)


## Normalizasyon Sorusu-2 ##

![image](https://user-images.githubusercontent.com/28144917/166876623-257a5299-f908-4832-9d4b-eadba598e91e.png)


> Yukarıdaki tabloyu  normalizasyon işlemlerini uygulayarak son haline getiriniz.

> ürün Sokları: Çanta(100 Adet), Cd(500 Adet), Kitap(325 Adet),Laptop(105 Adet),Defter(145 Adet)

## Normalizasyon Sorusu-2 Çö<üm ##

1. Adım						
tblSatış Tablosu						
SatisId	MusteriNo	MusteriAdi	ilAdi	Posta_Kodu	UrunAdı	UrunAdedi
1	1	Ayhan ERDEM	Adıyaman	2000	Çanta	5
2	1	Ayhan ERDEM	Adıyaman	2000	CD	200
3	1	Ayhan ERDEM	Adıyaman	2000	Kitap	3
4	2	Derya YAMAN	Aydın	5000	Çanta	10
5	3	Serdar AKIN	Bursa	1500	Laptop	5
6	4	Aylin KOTİL	İzmir	3000	Kitap	2
7	4	Aylin KOTİL	İzmir	3000	Defter	5
![image](https://user-images.githubusercontent.com/28144917/166876696-7b8f9001-d136-4e99-ada3-55e0b7d7ecc8.png)



