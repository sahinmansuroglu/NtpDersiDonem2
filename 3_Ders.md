## WPF nesnelerinin ortak Özellikleri ##
> WPF Uygulamarında kullanılan nesneler (Button, Label, TextBox, RadioButton vs) genişlik, yükseklik, arkaplan ve yazi rengi vb gibi bir çok ortak özelliğe sahiptir. Bu özellikler properties (Özellikler) penceresinden değiştirilebildiği gibi  XAML kodları üzerinden de değiştirilebilir. Ayrıca global veya locak stiller tanımlanıp istebilen nesnelere bu stiller verilebilir.

### 1. Name Özelliği ##
> Eklenen nesneye verilen isimdir. C# kodlarının bulunduğu arka planda nesnelere eişmek için bu isim kullanılır.

**Örnekler**
```xaml
        <Button x:Name="button1"/>
        <TextBox x:Name="textKutu1"/>
```
### 2. Height ve Width Özellikleri ##
> Eklenen nesnenin pixel cinsinden genişliğini ve yüksekliğini ayarlamak için kullanılır. 

**Örnekler**
```xaml
         <Button x:Name="button1" Height="40" Width="100"/>
         <TextBox x:Name="textKutu1" Height="50" Width="120"/>
```

### 3. Foreground ve Background Özellikleri ##
> Foreground ve Background Özelliği arkaplan ve ön plan rengini ayarlamak için kullanılır

**Örnekler**
```xaml
        <Button x:Name="button1" Foreground="Red" Background="Yellow"/>
        <TextBox x:Name="textKutu1" Foreground="Blue" Background="Yellow"/>
```

### 4. Content Özelliği ##
> Content özelliği, bir nesnenin yeteneklerine bağlı olarak ekranda ne göstereceğini ayarlama için kullanılır

**Örnekler**
```xaml
        <Button x:Name="button1" 
                Content="Tıklayınız.."
                Foreground="Red" 
                Background="Yellow"
                Width="100"
                Height="40"/>
     
```
**Ekran Görüntüsü**

![image](https://user-images.githubusercontent.com/28144917/152768421-8a5186c1-d269-4001-9b44-0ead8664b61b.png)

### 5. VerticalAlignment  ve HorizontalAlignment Özellikleri  ##
> VerticalAlignment  ve HorizontalAlignment Özellikleri  dikey ve yatay hizalama yapmak için kullanılır

| Yatay Hizalama Seçenekleri |Dikey Hizalama Seçenekleri|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/152773239-07048d68-f1b0-430f-a195-2e661a0878dd.png)      |![image](https://user-images.githubusercontent.com/28144917/152773532-67459cdb-5042-44b7-970d-089504eb9d8b.png)| 

**Örnekler**
| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/152774068-b2f1d14e-1a1c-4b0c-9205-cf8515b46228.png)|![image](https://user-images.githubusercontent.com/28144917/152774100-4f4cda04-bc1c-45be-9022-bf090c2bf52c.png)| 
|![image](https://user-images.githubusercontent.com/28144917/152774175-f9a53543-a149-419c-a418-0ddf4a50c882.png)| ![image](https://user-images.githubusercontent.com/28144917/152774204-c6d9454c-0195-4b9a-b4aa-791a5f1dd2bc.png)| 
|![image](https://user-images.githubusercontent.com/28144917/152774268-52e7de2d-ec1a-4519-8e30-8084d7cd7c1f.png)| ![image](https://user-images.githubusercontent.com/28144917/152774290-023c1206-d239-4bed-9ab8-df7d2804ad74.png)| 




### 6. Margin ##
> Margin özelliği bir nesnenin bulunduğu nesne içerisinde soldan, yukarıdan, sağdan ve aşağıdan uzaklığını ayarlamak için kullanılır.

**Örnekler**

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/152775445-2713f493-9e21-48c6-9cf4-a2bb0ace3114.png)|![image](https://user-images.githubusercontent.com/28144917/152775478-dc90799c-3b4d-47c3-8d9c-38679919afcc.png)| 
|![image](https://user-images.githubusercontent.com/28144917/152775586-0ce686d7-a588-4a03-9dae-9304d3b5d847.png)|![image](https://user-images.githubusercontent.com/28144917/152775620-64d9d29c-8584-460a-89d0-4f8c73626c41.png)| 
|![image](https://user-images.githubusercontent.com/28144917/152775718-0cd9bdef-a36b-4b79-97da-df0d1ebd4576.png)|![image](https://user-images.githubusercontent.com/28144917/152775745-f29cf2d1-267d-48b5-b177-dd7f653120e5.png)|

### 6. Padding ##
> Padding özelliği bir nesnenin içerisinde bulunan nesnelerin soldan, yukarıdan, sağdan ve aşağıdan uzaklığını ayarlamak için kullanılır.

**Örnekler**

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/152776972-9da05d46-6e23-4f82-8d78-b173f768e7f3.png)|![image](https://user-images.githubusercontent.com/28144917/152777007-391b7c75-2a18-45a1-882b-11b6e89ee15e.png)| 
|![image](https://user-images.githubusercontent.com/28144917/152777075-b3fb1739-d50d-41f6-b72d-d8ee68d6c44a.png)
|![image](https://user-images.githubusercontent.com/28144917/152777110-d49d840e-6dfe-46a2-84f8-e33d9dd4ca8f.png)| 
|![image](https://user-images.githubusercontent.com/28144917/152777267-2205f3e6-ad29-4fef-8d9a-f54572cc0074.png)|![image](https://user-images.githubusercontent.com/28144917/152777292-4c8fc95c-cdca-4ca7-9157-43a4f5e6b3b5.png)
| 
