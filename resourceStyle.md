## Resource dictionary İçerisinde Stil Oluşturma ##

> Arayüzlerimizdeki nesneleri görsel olarak ayrı ayrı biçimlendirmek yerine stiller oluşturarak  tek bir yerden bu biçimlendirmeyi yapabiliriz.

> Stil Oluşturmak İçin aşağıdaki örneği inceleyelim
```xaml
        <Style TargetType="Button">
            <Setter Property="Background" Value="Red"/>
        </Style>
 ```
 
  - TargetType: Biçimlendirilecek nesnenin tipi belirtmek için kullanılır.
  - Setter:  Özelliklere değer vermek için kullanılır
  
 > Yukarıdaki örnekte  uygulamamzdaki butonlar için bir stil oluşturulmuş ve "Background" özelliği  "Red" olarak ayarlanmıştır.
 

### Örnek-1 ###
> Aşağıdaki uygulamada Label nesneleri için bir Stil oluşturulmuştur. Oluşturulan bu stil Window içerisindeki tüm Label'lara etkilemiştir.

```xaml
<Window x:Class="WpfApp26.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp26"
        xmlns:sys="clr-namespace:System;assembly=mscorlib"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="300">

    <Window.Resources>
        
        <Style TargetType="Label">
            <Setter Property="Background" Value="LightPink"/>
            <Setter Property="Foreground" Value="DarkBlue"/>
            <Setter Property="BorderThickness" Value="5"/>
            <Setter Property="BorderBrush" Value="Purple"/>
        </Style>

    </Window.Resources>
    
    
    <Grid>
        <Label Content="Merhaba Dünya"
                HorizontalAlignment="Center"
               VerticalAlignment="Top"/>

        <Label Content="Metin 1" 
               HorizontalAlignment="Center"
               VerticalAlignment="Bottom"
        />
    </Grid>
</Window>

```

**Ekran Görüntüsü**

![image](https://user-images.githubusercontent.com/28144917/155081248-675a706f-f4d9-4c1f-beac-07aa8aaa2da7.png)



> Yukarıdaki Örnekte window içerisindeki tüm Label'ler aynı stillendirmeyi kullanmıştır. Eğer Window içerisinde herhangi bir nesne tür için birden fazla Stil tanımlamak istersek 
> Bunun için oluşturulan stile isim (key) verilebilir

```xaml
        <Style TargetType="Button" x:Key="MaviButonStyle">
            <Setter Property="Background" Value="blue"/>
        </Style>
        
        <Style TargetType="Button" x:Key="SariButonStyle">
            <Setter Property="Background" Value="yellow"/>
        </Style>
```
