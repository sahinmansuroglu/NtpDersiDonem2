## Trigger (Tetikleyici ) nedir?

> Trigger'lar temel olarak istenilen bir event (olay) gerçekleştiğinde belirlenen UI nesnelerinin property’lerini değiştirebilmemize olanak sağlar. Trigger'lar genellikle bir stil içersinde tanımlanırlar
> Üç Çeşit trigger yapısı bulunmaktadır Bunlar;

    1-Property trigger 
    2-Data Trigger 
    3-Event trigger 
 
 ### 1- Property Trigger ###
 > En yaygın kullanılan tetikleyici türü Property Trigger'dır ve <Trigger></trigger> tagları arasına tanımlanırlar.  Bu tetikleyici türü ile her hangi bir UI nesnesinin istenilen bir özelliğinini değişmesini yine aynı nesnenin başka bir özelliğinin istenilen bir değere ulaşmasına göre sağlıyabilirz.
    
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
