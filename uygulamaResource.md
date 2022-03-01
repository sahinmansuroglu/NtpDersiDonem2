## Resource Dictionary Kapsamı ##

>Kaynaklar (Resources), kaynak sözlüklerinde (Resource Dictionary) tanımlanır, ancak bir kaynak sözlüğünün tanımlanabileceği çok sayıda yer vardır. 

>Aşağıdaki örnekte, Pencere(Window) düzeyinde bir kaynak sözlüğü (Resource Dictionary) tanımlanmıştır ve bu sözlük içerisinde bir style tanımlanmıştır. Bu stil Pencere düzeyindeki bir sözlükde tanımlandığı için  sadece tanımlandığı pencere  içerisinde kullanılır. 

```xaml
<Window x:Class="WpfApp26.MainWindow"
        ........>

    <Window.Resources>
        
        <Style TargetType="Label" x:Key="labelStil">
            <Setter Property="Background" Value="LightPink"/>
            <Setter Property="Foreground" Value="DarkBlue"/>
            <Setter Property="BorderThickness" Value="5"/>
            <Setter Property="BorderBrush" Value="Purple"/>
        </Style>

    </Window.Resources>
    
    
    <Grid>
        <Label Content="Merhaba Dünya"  Style="{StaticResource labelStil}" />
        <Label Content="Metin 1"  Style="{StaticResource labelStil1}" />
    </Grid>
</Window>

```

### Kapsam Türleri ###
>Kapsam Türleri temel olarak aşağıdaki gibidir

  1. Uygulama Kapsamı (Application Level)
  2. Pencere/Sayfa Kapsamı (Window/Page Level)
  3. Element Kapsamı (Grid, StackPanel Gibi)

#### 1. Uygulama Kapsamı (Application Level) ####
>Aşağıdaki gibi App.xaml içerisinde tanımlanan kaynaklar tüm uygulama içerisinde kullanılır.

![image](https://user-images.githubusercontent.com/28144917/156135310-bfbe3545-a60b-4e3a-8856-bea6689eabe8.png)

#### 2. Pencere/Sayfa Kapsamı (Window/Page Level) ####
>Aşağıdaki gibi Window içerisinde tanımlanan kaynaklar sadece tanımlandığı Window içerisinde kullanılır.

![image](https://user-images.githubusercontent.com/28144917/156135612-80a71f09-4c91-4eb8-ac36-25a51c22403e.png)

#### 3. Element Kapsamı (Grid, StackPanel Gibi) ####

>Aşağıdaki gibi Grid  içerisinde tanımlanan kaynaklar sadece tanımlandığı Grid içerisinde kullanılır.

 ![image](https://user-images.githubusercontent.com/28144917/156136083-8956e675-4cb3-4cf8-b5a8-91b453378f5d.png)

>Aşağıdaki örnekte de StackPanel  içerisinde tanımlanan kaynaklar sadece tanımlandığı StackPanel içerisinde kullanılır.

![image](https://user-images.githubusercontent.com/28144917/156136428-c75e681c-5d64-46cf-bd34-c97c621a1bc3.png)


### Harici Kaynak Sözlüğü oluşturmak ###
> Harici kaynak Sözlüğü oluşturmak için aşağıdaki şekilde uygulamaya sözlük eklenebilir

![image](https://user-images.githubusercontent.com/28144917/156136860-1e0cab08-2b29-42e2-93dc-c5b55a8a553b.png)

> Ardından Aşağıdaki gibi istenilen kaynaklar sözlüğe eklenir

![image](https://user-images.githubusercontent.com/28144917/156137123-c5176844-7754-4ee4-a31c-abc77833f8ff.png)

### Harici Kaynak Sözlüğü Kullanmak ###

> Oluşturulan harici kaynak sözlüğünü kullanabilmek için kaynak sözlüğünün kullanılacağı yerde aşağıdaki çağrılması gerekir.

```xaml
 <(App/Window/Grid).Resources>
        <ResourceDictionary>
                    <ResourceDictionary.MergedDictionaries>
                        <ResourceDictionary Source="Dictionary1.xaml"/>
                    </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
  </(App/Window/Grid).Resources>
```


### Örnek-1 ###
> Aşağıda arayüzü ve xaml kodları verilen uygulamanın stillerini ayrı resource dictionary dosyasına ekleyiniz.  Ve bu dosyası Uygulama kapsamında projenize dahil ediniz.

[Tamamlanmış Proje Dosyası için Tıklayınız..](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8160994/WpfApp30.zip)

**Arayüz**

![image](https://user-images.githubusercontent.com/28144917/156149805-6ec5b622-1d4c-4d35-8170-a5776d0a6af0.png)

**XAML Kodları**

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


**Çözüm**

> **Dictionar1.xaml**

![image](https://user-images.githubusercontent.com/28144917/156156111-0b352447-ccfd-4b56-b683-31bdc33d58ca.png)

> **App.xaml**

![image](https://user-images.githubusercontent.com/28144917/156156291-74209e46-ec5a-4f30-8481-bb6a11c0b005.png)

> **MainWindow.xaml**

![image](https://user-images.githubusercontent.com/28144917/156156415-e1f17f1a-ab17-41a8-ad67-da2c046fef6e.png)




