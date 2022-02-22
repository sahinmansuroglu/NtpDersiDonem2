## Resource dictionary  (Kaynak Sözlüğü )Nedir? ##

> Resources, genellikle birden fazla kez kullanılması düşünülen  nesnelerin veya özelliklerin tanımlanmawsında kullanılır. Kullanıcı arayüzleri gibi  Resource Dictionary yapıları da XAML yapısında tanımlanmaktadır.

> Bir Resource oluşturmak ve  onu ileride kullanabilmek için key(anahtar) verilir. Bu anahtar aynı zamanda onun adı gibi de düşünelebilir.  

```xaml

      - <Window.Resources>…</Window.Resources> : Resource dictionary'nin tanımlanacağı yer
      - <sys:String x:Key="Mesaj">Merhaba Dünya</sys:String> : string tipinde Mesaj adında bir resource oluşturur.
      - {StaticResource Mesaj}: Mesaj adındaki anahtarın değerini herhangi bir UI nesnesinde  kullanılabilmemize olanak sağlar.
```

```xaml
      <Window x:Class="WpfApp26.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp26"
        xmlns:sys="clr-namespace:System;assembly=mscorlib"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">

    <Window.Resources>
        <sys:String x:Key="Mesaj">Merhaba Dünya</sys:String>
        <sys:String x:Key="Takimadi">Galatasaray</sys:String>
    </Window.Resources>
    
    
    <Grid>
        <Label Content="{StaticResource Mesaj}" HorizontalAlignment="Center"/>
        <Label Content="{StaticResource Takimadi}"/>
        <TextBox Text="{StaticResource Mesaj}" 
                 VerticalAlignment="Bottom"
                 Margin="10"/>
    </Grid>
</Window>
```
**Not:** String Tipinde veya diğer veri tiplerinde anahtar oluşturabilmek için window'a  xmlns:sys="clr-namespace:System;assembly=mscorlib" ad uzayının eklenmesi gerekir.

**Ekran Görüntüsü**

![image](https://user-images.githubusercontent.com/28144917/155069732-ed177fad-9703-473c-8c5a-fa3410241f9b.png)



https://docs.microsoft.com/en-us/windows/apps/design/style/xaml-resource-dictionary

https://www.codeproject.com/Tips/1205642/WPF-Resource-Dictionary-Basics

<Page.Resources>…</Page.Resources> - Defines the resource dictionary.
<x:String> - Defines the resource with the key "greeting".
{StaticResource greeting} - Looks up the resource with the key "greeting", which is assigned to the Text property of the TextBlock.

<Page
    x:Class="MSDNSample.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

    <Page.Resources>
        <x:String x:Key="greeting">Hello world</x:String>
        <x:String x:Key="goodbye">Goodbye world</x:String>
    </Page.Resources>

    <TextBlock Text="{StaticResource greeting}" Foreground="Gray" VerticalAlignment="Center"/>
</Page>


<Page
    x:Class="SpiderMSDN.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

    <Page.Resources>
        <SolidColorBrush x:Key="myFavoriteColor" Color="green"/>
        <x:String x:Key="greeting">Hello world</x:String>
    </Page.Resources>

    <TextBlock Foreground="{StaticResource myFavoriteColor}" Text="{StaticResource greeting}" VerticalAlignment="Top"/>
    <Button Foreground="{StaticResource myFavoriteColor}" Content="{StaticResource greeting}" VerticalAlignment="Center"/>
</Page>
