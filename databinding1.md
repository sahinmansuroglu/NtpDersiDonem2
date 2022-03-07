## Data-Binding nedir? ##

> Data-Binding, veriyi sağlayan  ile  veriyi kullanan kaynakları birbirine bağlayan ve bunları senkronize eden genel bir tekniktir.

### Basit Veri Bağlama Örneği ###

> Aşağıdaki örnekte label nesnesinin content'i txtAd isimli Textbox'ın Text özelliğine bağlanmıştır. Yani Text kutusuna ne yazılırsa aynı anda label'a da yazacaktır.

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

