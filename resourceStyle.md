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
> Aşağıdaki uygulamada Label nesneleri için bir Stil oluşturulmuştur. Oluşturulan bu stil Window içerisindeki tüm Label'ları etkilemiştir.

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




### Örnek-2 ###
> Aşağıdaki Örnek Bir önceki bölümde yapılmıştı. Ancak o uygulamada nesnelerin her bir özelliği için bir anahtar oluşturulmuştu.Şuan yapılacak olan uygulamada aynı arayüzü label'lar için kullanacağınız bir stil yanımlayarak gerçekleştiriniz.

**Bir Önceki bölümdeki uygulamanın Kaynak Sözlüğü (Resource Dictionary)**

![image](https://user-images.githubusercontent.com/28144917/156116721-dbb93f97-7b0c-4d11-99db-afaad5688711.png)

**Arayüz**

![image](https://user-images.githubusercontent.com/28144917/156116752-73f08578-255f-4729-92f1-25b5ae96084f.png)



**Çözüm**

```xaml
<Window x:Class="WpfApp29.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp29"
        xmlns:sys="clr-namespace:System;assembly=System.Runtime"
        mc:Ignorable="d"
        Title="MainWindow" Height="200" Width="550">
    <Window.Resources>

        <Style TargetType="Label">
            <Setter Property="Width" Value="150"/>
            <Setter Property="Height" Value="70"/>
            <Setter Property="Background" Value="DarkCyan"/>
            <Setter Property="Margin" Value="10 5 10 5"/>
        </Style>
        <sys:String x:Key="Mesaj">Merhaba 11ATBA </sys:String>
 
    </Window.Resources>   
    
    <Grid>
        <StackPanel Orientation="Horizontal">
            <Label Content="{StaticResource Mesaj}"/>
            <Label Content="{StaticResource Mesaj}" />
            <Label Content="{StaticResource Mesaj}"/>
        </StackPanel>
        
    </Grid>
</Window>

```

> Yukarıdaki Örnekte window içerisindeki tüm Label'ler aynı stillendirmeyi kullanmıştır. Eğer Window içerisinde herhangi bir nesne türü için birden fazla Stil tanımlamak istersek bunun için oluşturulan stile anahtar (key) verilebilir.

```xaml
        <Style TargetType="Label" x:Key="LabelStil1">
            <Setter Property="Width" Value="100"/>
            <Setter Property="Height" Value="50"/>
            <Setter Property="Background" Value="Red"/>
            <Setter Property="Margin" Value="30 15 10 5"/>
        </Style>
        
        <Style TargetType="Label" x:Key="LabelStil2">
            <Setter Property="Width" Value="150"/>
            <Setter Property="Height" Value="70"/>
            <Setter Property="Background" Value="DarkCyan"/>
            <Setter Property="Margin" Value="10 5 10 5"/>
        </Style>
```
