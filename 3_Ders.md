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

### 3. Content Özelliği ##
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

### 3. VerticalAlignment  ve HorizontalAlignment Özellikleri  ##
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


```xaml
        <Button x:Name="button1" Foreground="Red" Background="Yellow"/>
        <TextBox x:Name="textKutu1" Foreground="Blue" Background="Yellow"/>
```

### 3. Margin ##
> Margin özelliği bir nesnenin bulunduğu nesne içerisinde soldan, üstten, sağdan ve aşağıdan uzaklığını ayarlamak için kullanılır.

**Örnekler**
```xaml
        <Button x:Name="button1" Foreground="Red" Background="Yellow"/>
        <TextBox x:Name="textKutu1" Foreground="Blue" Background="Yellow"/>
```
