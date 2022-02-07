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
### 3. VerticalAlignment ve HorizontalAlignment Özellikleri  ##
> Margin özelliği bir nesnenin bulunduğu nesne içerisinde soldan, üstten, sağdan ve aşağıdan uzaklığını ayarlamak için kullanılır.

**Örnekler**
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
