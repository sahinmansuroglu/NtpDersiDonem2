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
> Aşağıdaki Örnek Bir önceki bölümde yapılmıştı. Ancak o uygulamada nesnelerin her bir özelliği için bir anahtar oluşturulmuştu.Şuan yapılacak olan uygulamada aynı arayüzü label'lar için kullanacağınız bir stil tanımlayarak gerçekleştiriniz.

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

> Yukarıda LabelStil1 ve LabelStil2 adında iki tane stil oluşturulmuştur. Bu stillerden birini aşağıdaki gibi herhangi bir label'a verebiliriz.

```xaml
        <Label Content="Merhaba Dünya" Style="{StaticResource labelStil1}"/>
        <Label Content="Merhaba 11 ATBA"  Style="{StaticResource labelStil2}"/>
```

### Örnek-3  ###

> Aşağıdaki arayüzü label için 2 farklı Stil oluşturarak tasarlayınız.

![image](https://user-images.githubusercontent.com/28144917/156128956-9e981dc3-736f-4fbd-b985-09eea5365013.png)

**Cevap**
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

        <Style TargetType="Label" x:Key="labelStil1">
            <Setter Property="Width" Value="150"/>
            <Setter Property="Height" Value="70"/>
            <Setter Property="Background" Value="DarkCyan"/>
            <Setter Property="Margin" Value="10 5 10 5"/>
        </Style>
        
        <Style TargetType="Label" x:Key="labelStil2">
            <Setter Property="Width" Value="100"/>
            <Setter Property="Height" Value="70"/>
            <Setter Property="Background" Value="Red"/>
            <Setter Property="Margin" Value="10 5 10 5"/>
        </Style>
        
        <sys:String x:Key="Mesaj">Merhaba 11ATBA </sys:String>
 
    </Window.Resources>   
    
    <Grid>
        <StackPanel Orientation="Horizontal">
            <Label Content="{StaticResource Mesaj}"
                   Style="{StaticResource labelStil1}"/>
            <Label Content="{StaticResource Mesaj}"
                   Style="{StaticResource labelStil2}"/>
            <Label Content="{StaticResource Mesaj}"
                    Style="{StaticResource labelStil1}"/>
        </StackPanel>
        
    </Grid>
</Window>

```

### Örnek-4  ###
> Aşağıdaki Görseli verilen arayüzü button için 2 farklı stil kullanarak tasarlayınız.

![image](https://user-images.githubusercontent.com/28144917/156530868-8c007fe7-3f86-43f5-b1b1-c09547b0b8e2.png)

```xaml
<Window x:Class="WpfApp33.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp33"
        xmlns:sys="clr-namespace:System;assembly=System.Runtime"
        mc:Ignorable="d"
        Title="MainWindow" Height="200" Width="450">
    <Window.Resources>
        <Style TargetType="Button" x:Key="butonStil1">
            <Setter Property="Height" Value="40"/>
            <Setter Property="Padding" Value="20 5 20 5"/>
            <Setter Property="Margin" Value="10 5 10 5"/>
            <Setter Property="Background" Value="Red"/>
            <Setter Property="Foreground" Value="Yellow"/>
            <Setter Property="FontWeight" Value="Bold"/>
        </Style>
        <Style TargetType="Button" x:Key="butonStil2">
            <Setter Property="Height" Value="40"/>
            <Setter Property="Padding" Value="20 5 20 5"/>
            <Setter Property="Margin" Value="10 5 10 5"/>
            <Setter Property="Background" Value="Yellow"/>
            <Setter Property="Foreground" Value="Red"/>
            <Setter Property="FontWeight" Value="Bold"/>
        </Style>

    </Window.Resources>
    <WrapPanel Orientation="Horizontal">
        <Button Content="Buton 1"
                Style="{StaticResource butonStil1}"/>
        <Button Content="Buton 2"
                Style="{StaticResource butonStil2}"/>
        <Button Content="Buton 3"
                Style="{StaticResource butonStil2}"/>
        <Button Content="Buton 4"
                Style="{StaticResource butonStil1}"/>
        <Button Content="Buton 1"
                Style="{StaticResource butonStil1}"/>
        <Button Content="Buton 2"
                Style="{StaticResource butonStil2}"/>
        <Button Content="Buton 3"
                Style="{StaticResource butonStil2}"/>
        <Button Content="Buton 4"
                Style="{StaticResource butonStil1}"/>
    </WrapPanel>
</Window>

```

### Örnek-5  ###
> Aşağıdaki Görseli verilen arayüzü textbox Button ve Label ve Radio button için oluşturacağınız özel stilleri kullanarak tasarlayınız


![image](https://user-images.githubusercontent.com/28144917/156149805-6ec5b622-1d4c-4d35-8170-a5776d0a6af0.png)

Not:En Dışta Group box olacaktır. Temel Kullanımı Aşağıdadır.

![image](https://user-images.githubusercontent.com/28144917/156128605-8d333b7f-dce7-4934-b3f4-bc3c76b07578.png)


**Cevap**
```xaml
<Window x:Class="WpfApp30.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp30"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="520">
    <Window.Resources>
        <Style TargetType="GroupBox">
            <Setter Property="Margin" Value="10"/>
            <Setter Property="BorderBrush" Value="DarkGreen"/>
            <Setter Property="BorderThickness" Value="2"/>
            <Setter Property="FontSize" Value="15"/>
        </Style>
        
        <Style TargetType="Button">
            <Setter Property="Margin" Value="4"/>
            <Setter Property="Padding" Value="18 5 17 5"/>
            
        </Style>

        <Style TargetType="Label">
            <Setter Property="FontWeight" Value="Normal"/>
            <Setter Property="Foreground" Value="DarkSlateGray"/>
        </Style>

        <Style TargetType="TextBox">
            <Setter Property="Margin" Value="5"/>
            <Setter Property="Height" Value="35"/>
        </Style>

        <Style TargetType="RadioButton" x:Key="rbEvetStil">
            <Setter Property="FontWeight" Value="Bold"/>
            <Setter Property="Margin" Value="5"/>
            <Setter Property="VerticalContentAlignment" Value="Center"/>
            <Setter Property="Foreground" Value="Red"/>
        </Style>
        <Style TargetType="RadioButton" x:Key="rbHayirStil">
            <Setter Property="FontWeight" Value="Bold"/>
            <Setter Property="Margin" Value="5"/>
            <Setter Property="VerticalContentAlignment" Value="Center"/>

        </Style>
    </Window.Resources>

    <GroupBox Header="İşlem Bilgileri">
        <StackPanel Margin="5" >
            <Label Content="İşlem açıklaması"/>
            <TextBox />
            <StackPanel Orientation="Horizontal">
                <Label Content="Kullanılan Kağıt Sayısı Günlük toplama Eklensin mi?"/>
                <RadioButton Content="Evet"
                             Style="{StaticResource rbEvetStil}"/>
                <RadioButton Content="Hayır" IsChecked="True"
                             Style="{StaticResource rbHayirStil}"/>
            </StackPanel>
            <Label Content="Fişde Gözükecek Kısa Açıklama"/>
            <TextBox/>
            <StackPanel Orientation="Horizontal">
                <Button Content="Yeni İşlem Ekle"/>
                <Button Content="Seçili İşlemi Sil"/>
                <Button Content="Güncelle"/>
                <Button Content="Temizle"/>
            </StackPanel>

        </StackPanel>
        
        
    </GroupBox>
    
</Window>

```


### Örnek-5  ###
> Aşağıdaki Görseli verilen arayüzü   oluşturacağınız özel stilleri kullanarak tasarlayınız.


![image](https://user-images.githubusercontent.com/28144917/156565639-ae444e50-98cc-4a21-a6c8-6ec2ac199925.png)


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
        <Style TargetType="Border" x:Key="disBorder">
            <Setter Property="Margin" Value="10"/>
            <Setter Property="BorderThickness" Value="2"/>
            <Setter Property="BorderBrush" Value="LightBlue"/>
            <Setter Property="CornerRadius" Value="10"/>


        </Style>
        <Style TargetType="Border" x:Key="puanBorder">
            <Setter Property="Margin" Value="3"/>
            <Setter Property="BorderThickness" Value="2"/>
            <Setter Property="BorderBrush" Value="LightBlue"/>
            <Setter Property="CornerRadius" Value="10"/>


        </Style>
        <Style TargetType="Border" x:Key="ListBoxBorder">
            <Setter Property="Margin" Value="3"/>
            <Setter Property="BorderThickness" Value="2"/>
            <Setter Property="BorderBrush" Value="LightBlue"/>
            <Setter Property="CornerRadius" Value="10"/>
       </Style>

        <Style TargetType="Label" x:Key="labelBaslik">
            <Setter Property="VerticalAlignment" Value="Center"/>
            <Setter Property="HorizontalAlignment" Value="Right"/>
            <Setter Property="FontWeight" Value="Bold"/>
            <Setter Property="Foreground" Value="DarkSlateGray"/>
        </Style>

        <Style TargetType="TextBox" x:Key="textBoxStil">
         
            <Setter Property="Margin" Value="5"/>
            
        </Style>


        <Style TargetType="Label" x:Key="labelPuanlar">
            <Setter Property="VerticalAlignment" Value="Center"/>
            <Setter Property="HorizontalAlignment" Value="Center"/>
            <Setter Property="Margin" Value="5 0 5 0"/>
            <Setter Property="Width" Value="90"/>
            <Setter Property="FontWeight" Value="Bold"/>
            <Setter Property="Foreground" Value="DarkSlateGray"/>
            <Setter Property="HorizontalContentAlignment" Value="Center"/>
        </Style>

        <Style TargetType="TextBox" x:Key="textPuanlar">
            <Setter Property="VerticalAlignment" Value="Center"/>
            <Setter Property="HorizontalAlignment" Value="Center"/>
            <Setter Property="Width" Value="90"/>
            <Setter Property="FontWeight" Value="Bold"/>
            <Setter Property="Foreground" Value="DarkSlateGray"/>
            <Setter Property="Margin" Value="5 0 5 0"/>

        </Style>

        <Style TargetType="Button" x:Key="butonStil">
            
            
            <Setter Property="FontWeight" Value="Bold"/>
            <Setter Property="Foreground" Value="DarkSlateGray"/>
            <Setter Property="Margin" Value="7"/>

        </Style>

    </Window.Resources>
    <Border Style="{StaticResource disBorder}">
        <Grid Margin="10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="1*"/>
                <ColumnDefinition Width="1*"/>
                <ColumnDefinition Width="1*"/>
                <ColumnDefinition Width="*"/>
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition Height="40"/>
                <RowDefinition Height="40"/>
                <RowDefinition Height="60"/>
                <RowDefinition Height="50"/>
                <RowDefinition Height="1*"/>
            </Grid.RowDefinitions>
            <Label Content="Ad:" Grid.Row="0" Grid.Column="0"
                   Style="{StaticResource labelBaslik}"/>
            <Label Content="Soyad:" Grid.Row="0" Grid.Column="2"
                    Style="{StaticResource labelBaslik}"/>
            <Label Content="Yaş:" Grid.Row="1" Grid.Column="0"
                    Style="{StaticResource labelBaslik}"/>
            <Label Content="Okul No:" Grid.Row="1" Grid.Column="2"
                    Style="{StaticResource labelBaslik}"/>
            <Label Content="Puanlar:" Grid.Row="2" Grid.Column="0"
                    Style="{StaticResource labelBaslik}"/>
            <TextBox x:Name="txtAd" Grid.Row="0" Grid.Column="1"
                      Style="{StaticResource textBoxStil}"/>
            <TextBox x:Name="txtSoyad" Grid.Row="0" Grid.Column="3"
                       Style="{StaticResource textBoxStil}"/>
            <TextBox x:Name="txtYas" Grid.Row="1" Grid.Column="1"
                       Style="{StaticResource textBoxStil}"/>
            <TextBox x:Name="txtOkulNo" Grid.Row="1" Grid.Column="3"
                       Style="{StaticResource textBoxStil}"/>

            <Border Grid.Row="2" 
                    Grid.Column="1" 
                    Grid.ColumnSpan="3"
                    Style="{StaticResource puanBorder}">
                <StackPanel Orientation="Vertical">
                    <StackPanel Orientation="Horizontal">
                        <Label Content="1. Yazılı"
                               Style="{StaticResource labelPuanlar}"/>
                        <Label Content="2. Yazılı"
                               Style="{StaticResource labelPuanlar}"/>
                        <Label Content="1. Perf"
                               Style="{StaticResource labelPuanlar}"/>
                        <Label Content="2. Perf"
                               Style="{StaticResource labelPuanlar}"/>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <TextBox x:Name="txtYazili1"
                                  Style="{StaticResource textPuanlar}"/>
                        <TextBox x:Name="txtYazili2"
                                  Style="{StaticResource textPuanlar}"/>
                        <TextBox x:Name="txtPerf1"
                                  Style="{StaticResource textPuanlar}"/>
                        <TextBox x:Name="txtPerf2"
                                 Style="{StaticResource textPuanlar}"/>
                    </StackPanel>
                </StackPanel>
                
            </Border>

            <Button x:Name="btnEkle" Content="Ekle" Grid.Row="3" Grid.Column="0"
                    Style="{StaticResource butonStil}"
                    Click="btnEkle_Click"/>
            <Button x:Name="btnSil" Content="Sil" Grid.Row="3" Grid.Column="1"
                    Style="{StaticResource butonStil}"
                    Click="btnSil_Click"/>
            <Button x:Name="btnAra" Content="Ara" Grid.Row="3" Grid.Column="2"
                    Style="{StaticResource butonStil}"/>
            <Button x:Name="btnGuncelle" Content="Guncelle" Grid.Row="3" Grid.Column="3"
                    Style="{StaticResource butonStil}"/>

            <Border Style="{StaticResource ListBoxBorder}" 
                    Grid.Column="0"
                    Grid.Row="4"
                    Grid.ColumnSpan="4">
                <ListBox x:Name="lbOgrenciler" Margin="5" BorderThickness="0">
                    
                </ListBox>
                
                
            </Border>
        </Grid>
        
    </Border>
</Window>

```
