## Data-Binding nedir? ##

> Data-Binding, veri nesnelerini UI nesneleri içerisinde görüntülemeye ve bu verileri bir birleriyle senkronize olmasını sağlayan genel bir tekniktir.

### Basit Veri Bağlama Örneği ###

> Aşağıdaki örnekte label nesnesinin content'i txtAd isimli Textbox'ın Text özelliğine bağlanmıştır. Yani Text kutusuna ne yazılırsa aynı anda label'da da görüntülenecektir.

```xaml
    <Label Content="{Binding Path=Text, ElementName=txtAd}" />
```   
> Uygulamanın tamamlanmış Hali

![image](https://user-images.githubusercontent.com/28144917/157036442-8a0df817-97eb-48e2-871f-39ae39b75b3a.png)

```xaml
<Window x:Class="WpfApp7.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp7"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="300">

    
    <StackPanel Margin="10">
        
            <Label Content="Ad" />
            <TextBox Name="txtAd" />
            <StackPanel Orientation="Horizontal">
                <Label Content="Merhaba " />
                <Label Content="{Binding Path=Text, ElementName=txtAd}" />
             </StackPanel>

    </StackPanel>
</Window>


```

### Örnek-1 ###
> Aşağıdaki arayüzü tasarlayarak rectangle nesnesinin genişlik, yükseklik ve dolgu rengini ilgili textBox'lara bağlayınız

![image](https://user-images.githubusercontent.com/28144917/157038185-8147b9ac-e034-4d10-85d8-248accdde715.png)

**Çözüm**

```xaml
<Window x:Class="WpfApp7.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp7"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="300">

    <Window.Resources>
        <Style TargetType="TextBox">
            <Setter Property="Margin" Value="5"/>
        </Style>
    </Window.Resources>
    


    
    <StackPanel Margin="1" >
        
            <Label Content="Genişlik " />
            <TextBox Name="txtGenislik" />
            <Label Content="Yükselik " />
            <TextBox Name="txtYukseklik" />
            <Label Content="Yükselik " />
            <TextBox Name="txtRenk" />

        <Rectangle Width="{Binding Path=Text, ElementName=txtGenislik}"
                   Height="{Binding Path=Text, ElementName=txtYukseklik}"
                   Fill="{Binding Path=Text, ElementName=txtRenk}"/>



    </StackPanel>
</Window>

```
### OneWay ve TwoWay Binding ###
> **OneWay (Tek Yönlü)** binding ile  veri kaynağında bir değişim olduğunda  bu değişiklik verinin kullanıldığı yerde gözlenir. Ancak verinin kullanıldığı yerde veri üzerinde bir değişiklik yapılırsa bu veri kaynağındaki veri güncellenmez.

> **TwoWay (İki Yönlü**) binding ile  veri kaynağında bir değişim olduğunda  bu değişiklik verinin kullanıldığı yerde gözlenir.Ayrıca OneWay'den farklı olarak   verinin kullanıldığı yerde  veri üzerinde bir değişiklik yapılırsa bu değişiklik veri kaynağındaki veriyide etkileyecektir.


> Aşağıdaki Örnekte  txtMetin1'nin Text Özelliği txtMetin1'in Text zelliğine OneWay olarak bağlanmıştır. Yani txtMetin1 kutusuna bir metin yazıldığında aynı anda bu metin txtMetin2'de de görüntülenecektir. Ancak tersi durum söz konusu olmayacaktır.
```xaml
        <Label Content="Metin 1 " />
        <TextBox Name="txtMetin1"  />
        <Label Content="Metin 2 " />
         <TextBox Name="txtMetin2" Text="{Binding Path=Text, ElementName=txtMetin1, Mode=OneWay}" />
```

> Aşağıdaki Örnekte  txtMetin1'nin Text Özelliği txtMetin1'in Text zelliğine TwoWay olarak bağlandığı için  txtMetin1 kutusuna girilen metin txtMetin2 kutusunda, txtMetin2 kutusuna girilen metin  ise txtMetin1 kutusunda görüntülenecektir. 

```xaml
        <Label Content="Metin 1 " />
        <TextBox Name="txtMetin1"  />
        <Label Content="Metin 2 " />
         <TextBox Name="txtMetin2" Text="{Binding Path=Text, ElementName=txtMetin1, Mode=OneWay}" />
```

### OneWayToSource ve OneTime Binding ###
> **OneWayToSource** ile OneWay yönünün tersi yönde bağlama sağlar. Yani OneWay'de kaynakta değişiklik olduğunda hedefte bu değişikli gözlenirken  OneWayToSource'de bunun tersi yönde gerçekleşir.

> **OneTime** ile bağlama işlemi sadece uygulama ilk başlatıldığında gerçekleşir

### UpdateSourceTrigger ###
> **UpdateSourceTrigger** ile veri kaynağının henagi durumda güncelleneceği belirlenir. 

> **UpdateSourceTrigger=PropertyChanged** olarak ayarlanırsa property'de herhangi bir değişiklik olduğunda bu değişiklik kaynağa iletilir.

> **UpdateSourceTrigger=LostFocus** olarak ayarlanırsa bağlama yapılan nesneden başka bir nesneye geçiş yapıldığında property'deki değişiklik  kaynağa iletilir.

Bursada Slider Örneği Yap
