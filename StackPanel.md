## StackPanel Kullanımı ##

> StackPanel, içerisine yerleştirilmiş nesneleri yatay veya dikey olarak hizalamaya yarayan bir paneldir. 

**Örnekler**

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/153183609-44a585ff-ad95-40a5-bd9d-944c07129081.png)|![image](https://user-images.githubusercontent.com/28144917/153183661-03dbbb6c-8aec-461b-8362-90273c98decb.png)|
|![image](https://user-images.githubusercontent.com/28144917/153183777-293bd462-9450-417a-9b7c-b85144fa9d27.png)|![image](https://user-images.githubusercontent.com/28144917/153183858-83e28d5d-e5af-48d5-b8c8-78d84829a19f.png)|
|![image](https://user-images.githubusercontent.com/28144917/153190298-6c2cdb64-bc34-4e7e-b3a8-68f9505ea996.png)|![image](https://user-images.githubusercontent.com/28144917/153190336-a2836d68-f27c-4c1d-bcfc-59f9ff9b0fed.png)|
|||
|||


**Örnek**

![image](https://user-images.githubusercontent.com/28144917/153192812-2990ed51-6509-498c-bfe5-cbc0d9780cbd.png)


```csharp
<Window x:Class="WpfApp2.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp2"
        mc:Ignorable="d"
        Title="MainWindow" Height="300  " Width="300" >
    <StackPanel Margin="30">
        <Label Content="Lütfen Favori  Spor Dalınızı Seçiniz." FontSize="14"/>
        <RadioButton Margin="15,15,0,0">Basketbol</RadioButton>
        <RadioButton Margin="15,15,0,0">Futbol</RadioButton>
        <RadioButton Margin="15,15,0,0">Voleybol</RadioButton>
        <StackPanel Orientation="Horizontal" HorizontalAlignment="Center">
            <Button Content="Oyla" Margin="5" MinWidth="60"></Button>
            <Button Content="Çıkış" Margin="5" MinWidth="60"></Button>
        </StackPanel>
    </StackPanel>
</Window>

```

