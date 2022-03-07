## Trigger (Tetikleyici ) nedir?

> Trigger'lar temel olarak istenilen bir event (olay) gerçekleştiğinde belirlenen UI nesnelerinin property’lerini değiştirebilmemize olanak sağlar. Trigger'lar genellikle bir stil içersinde tanımlanırlar
> Üç Çeşit trigger yapısı bulunmaktadır Bunlar;

    1-Property trigger 
    2-Data Trigger 
    3-Event trigger 
 
 ### 1- Property Trigger ###
 > En yaygın kullanılan tetikleyici türü Property Trigger'dır ve <Trigger></trigger> tagları arasına tanımlanırlar.  Bu tetikleyici türü ile her hangi bir UI nesnesinin istenilen bir özelliğinini değişmesini yine aynı nesnenin başka bir özelliğinin istenilen bir değere ulaşmasına göre sağlıyabilirz.
    

> Aşağıda tanımlanan stil içerisinden bir trigger tanımlanmıştır. Bu trigger "IsMouseOver" property'si "true" olduğunda tetiklenerek "foregorund" property'sini red yapmıştır. Yani  bu stile sahip bir butonun üzerine mouse ikonunu getirdiğimizde yazı rengi kırmızı olmuştur.

```xaml

        <Style x:Key = "ButonStil" TargetType = "Button">
            <Setter Property = "Foreground" Value = "Blue" />
            <Setter Property = "FontSize" Value = "15" />
            <Style.Triggers>
                <Trigger Property = "IsMouseOver" Value = "True">
                    <Setter Property = "Foreground" Value = "red" />
                </Trigger>
            </Style.Triggers>
        </Style>
```

> Uygulamanın tamamlanmış Hali Aşağıdadır.
    
```xaml
    <Window x:Class="WpfApp10.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp10"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <Window.Resources>

        <Style x:Key = "ButonStil" TargetType = "Button">
            <Setter Property = "Foreground" Value = "Blue" />
            <Setter Property = "FontSize" Value = "15" />
            <Style.Triggers>
                <Trigger Property = "IsMouseOver" Value = "True">
                    <Setter Property = "Foreground" Value = "red" />
                </Trigger>
            </Style.Triggers>
        </Style>
    </Window.Resources>
    
    <Grid>
        <Button  Margin="50" Style="{StaticResource ButonStil}">
            Tıklayınız
        </Button>
    </Grid>
</Window>
```


#### Örnek-1 ####
> Content'i "En Büyük İçel İdman Yurdu" olan bir label ekleyiniz. Label'in arkaplanı mavi yazı rengi kırmızı olsun. Bir Trigger oluşturarak label'in üzerine gelindiğinde yazı rengini mavi arkaplanı kırmızı olmasını sağlayınız.

**Çözüm**

```xaml
<Window x:Class="WpfApp35.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp35"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="600">
    
    
    <Window.Resources>

        <Style x:Key = "labelStil" TargetType = "Label">
            <Setter Property = "Foreground" Value = "Red" />
            <Setter Property = "Background" Value = "Blue" />
            <Setter Property = "FontSize" Value = "15" />
            <Style.Triggers>
         
                <Trigger Property = "IsMouseOver" Value = "True">

                    <Setter Property = "Foreground" Value = "Blue" />
                    <Setter Property = "Background" Value = "Red" />
                </Trigger>
                
            </Style.Triggers>
            

            
        </Style>
        
    </Window.Resources>
    
    <Border>
        <Label Margin="50" Style="{StaticResource labelStil}">
            En Büyük İçel İdman Yurdu
        </Label>

    </Border>
</Window>

```
