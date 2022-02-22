## Resource dictionary  (Kaynak Sözlüğü )Nedir? ##

> Resources, genellikle birden fazla kez kullanmayı düşündüğümüz bazı nesnelerin tanımlarıdır. Kullanıcı arayüzlerini gibi  Resource Dictionary yapıları da
> XAML yapısında tanımlanamkatadır.
> Bir Resource oluşturmak için ileri de onu çağırmak için kullanacağımız bir anahtar  seçilir. Bu anahtar aynı zamanda onun adı gibi de düşünelebilir.  
> Daha sonra bir XAML kaynağına başvurmak için, adı gibi davranan bir kaynak için bir anahtar belirtirsiniz.



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
