## 4. ve  5. Bölüm Quiz Sorusu ##

Quiz ile ilgili Sorularınız İçin  12.03.2022 Cumartesi Saat 20:30 da zoom toplantısı yapacağız. Aşağıdaki linki Kullanabilirsiniz.

Şahin Mansuroğlu sizi planlanmış Zoom toplantısına davet ediyor.

Konu: Şahin Mansuroğlu's Personal Meeting Room

Zoom Toplantısına Katılın
https://us04web.zoom.us/j/3691187014?pwd=Rk84Z3ZoMkNQc2tEbFpzbGVXUkRzQT09

Toplantı Kimliği: 369 118 7014
Parola: MTAL0033



**Arayüz:** 20 Puan

**C# Kodları:** 20 Puan

> [**Quiz Sorusu ile ilgili Açıklama Videosunu izlemek için Tıklayınız**](https://www.youtube.com/watch?v=2d9kE8nBmwA)


> [Uygulamanın Tamamlanmış Halini indirmek için Tıklayınız..](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8234500/WpfApp12.zip)


| Ekran Görüntüsü |
|:--------:|
|![image](https://user-images.githubusercontent.com/28144917/157929535-6290584e-8c09-4855-bcbc-957b61267aec.png)|


| Uygulamanın Çalışan Halinin Ekran Görüntüsü |
|:--------:|
|![image](https://user-images.githubusercontent.com/28144917/157930675-93521ab3-d544-47a6-a702-714f9d368be8.png)|

<table>
<tr>
<th>
Kullanıcı Arayüzün XAML kodları
</th>
</tr>
      <tr>
                <td>
                  
                  
```xaml
<Window x:Class="WpfApp12.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp12"
        mc:Ignorable="d"
        Title="Databinding ve Trigger Örneği" Height="480" Width="600" ResizeMode="NoResize">
    <Window.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <ResourceDictionary Source="Dictionary1.xaml"/>
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Window.Resources>
    
    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="283*"/>
            <ColumnDefinition Width="317*"/>
        </Grid.ColumnDefinitions>

        <StackPanel x:Name="stkPanel1" Grid.Row="0" Grid.Column="0" Margin="10" >
            <Label Content="Genişlik " Style="{StaticResource labelStil}" />
            <Slider x:Name="sldrGenislik" 
                    Minimum="0" Maximum="200"
                    Value="{Binding ElementName=txtGenislik, Path=Text,UpdateSourceTrigger=PropertyChanged,Mode=TwoWay}"    
                    Style="{StaticResource sliderStil}"
                    IsSnapToTickEnabled="True"/>
            <TextBox Name="txtGenislik" 
                     Text="{Binding Path=Genislik,UpdateSourceTrigger=PropertyChanged}" 
                     Style="{StaticResource textBoxStil}"/>



            <Label Content="Yükseklik " Style="{StaticResource labelStil}" />
            <Slider x:Name="sldrYukseklik" 
                    Minimum="0" Maximum="200"
                    Value="{Binding ElementName=txtYukseklik, Path=Text,UpdateSourceTrigger=PropertyChanged,Mode=TwoWay}"     
                    Style="{StaticResource sliderStil}"
                    IsSnapToTickEnabled="True"/>

            <TextBox Name="txtYukseklik" 
                     Text="{Binding Path=Yukseklik,UpdateSourceTrigger=PropertyChanged}" 
                      Style="{StaticResource textBoxStil}"/>

            <Label Content="Dolgu Rengi"  Style="{StaticResource labelStil}" />

            <TextBox  Name="txtDolguRengi"  
                      Text="{Binding Path=DolguRengi, UpdateSourceTrigger=PropertyChanged}"
                       Style="{StaticResource textBoxStil}"/>
            
            <ListBox x:Name="listBoxDikdortgenler" Height="140"  
                     SelectionChanged="listBoxDikdortgenler_SelectionChanged" 
                      Style="{StaticResource listBoxStil}"/>
        </StackPanel>
        <Border Grid.Column="1" Style="{StaticResource BorderStil}">
            
             <Rectangle 
                    Width="{Binding Path=Text, ElementName=txtGenislik}"
                    Height="{Binding Path=Text, ElementName=txtYukseklik}"
                     Fill="{Binding Path=Text, ElementName=txtDolguRengi}"/>
            
        </Border>
       

    </Grid>
</Window>


```
                  
                  
</td>
</tr>
</table>




<table>
<tr>
<th>
Dikdorgen sınıfının bulunduğu Dikdortgen.cs dosyası
</th>
</tr>
<tr>
<td>

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Text;

namespace WpfApp12
{
    class Dikdortgen:INotifyPropertyChanged
    {
        private int genislik;

        public int Genislik
        {
            get { return genislik; }
            set { 
                genislik = value;
                OnPropertyChanged("Genislik");
                OnPropertyChanged("GozukecekMetin");
            }
        }
        private int yukseklik;

        public int Yukseklik
        {
            get { return yukseklik; }
            set {
                yukseklik = value;
                OnPropertyChanged("Yukseliklik");
                OnPropertyChanged("GozukecekMetin");

            }
        }

        private string dolguRengi;

        public string DolguRengi
        {
            get { return dolguRengi; }
            set {
                dolguRengi = value;
                OnPropertyChanged("DolguRengi");
                OnPropertyChanged("GozukecekMetin");
            }
        }
       

        public string GozukecekMetin 
        {  
            get { return $"G:{genislik,-5}   Y:{yukseklik,-5}   R:{DolguRengi}"; }
            
        }


        protected internal virtual void OnPropertyChanged(string propertyName)
        {
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
        }

        public event PropertyChangedEventHandler PropertyChanged;

    }
}


```
                                    
                                    

</td>
</tr>
</table>




<table>
<tr>
<th>
Kullanıcı arayüzünün Arkaplanında  çalışan C# kodları
</th>
</tr>
<tr>
<td>
      
      
```csharp
using System;
using System.Collections.Generic;
using System.Collections.ObjectModel;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

namespace WpfApp12
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        Dikdortgen dikdortgen;
        ObservableCollection<Dikdortgen> dikdortgenler = new ObservableCollection<Dikdortgen>();
        public MainWindow()
        {
            InitializeComponent();
          
           

            dikdortgenler.Add(new Dikdortgen
            {
                Genislik = 100,
                Yukseklik = 100,
                DolguRengi = "Red"
            });
            dikdortgenler.Add(new Dikdortgen
            {
                Genislik = 80,
                Yukseklik = 70,
                DolguRengi = "Blue"
            });
            dikdortgenler.Add(new Dikdortgen
            {
                Genislik = 100,
                Yukseklik = 100,
                DolguRengi = "Brown"
            });
            dikdortgenler.Add(new Dikdortgen
            {
                Genislik = 40,
                Yukseklik = 60,
                DolguRengi = "Green"
            });

            listBoxDikdortgenler.ItemsSource= dikdortgenler;
            listBoxDikdortgenler.DisplayMemberPath = "GozukecekMetin";
        }

        private void listBoxDikdortgenler_SelectionChanged(object sender, SelectionChangedEventArgs e)
        {
            
            stkPanel1.DataContext = (Dikdortgen)listBoxDikdortgenler.SelectedItem;
        }
    }
}

```
      
      
</td>
</tr>
</table>

      
      <table>
<tr>
<th>
Kullanıcı Arayüzünde kullanılan Stillerin bulunduğu Dictionary1.xaml isimli Resource Dictionary dosyasının XAML kodları
</th>
</tr>
<tr>
<td>

      
```xaml
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <SolidColorBrush x:Key="CustomSliderBackgroundSolidColorBrush" Color="#1E211B" />

    <LinearGradientBrush x:Key="CustomSliderForegroundBrush" StartPoint="0,0" EndPoint="0,1">
        <GradientStop Color="#65351F" Offset="0.2" />
        <GradientStop Color="#9B5B2B" Offset="0.5" />
        <GradientStop Color="#65351F" Offset="0.8" />
    </LinearGradientBrush>

    <LinearGradientBrush x:Key="CustomSliderThumBrush" StartPoint="0,0" EndPoint="0,1">
        <GradientStop Color="#3B3C39" Offset="0.2" />
        <GradientStop Color="#454543" Offset="0.5" />
        <GradientStop Color="#3B3C39" Offset="0.8" />
    </LinearGradientBrush>

    <Style x:Key="CustomSliderThumbStyle" TargetType="{x:Type Thumb}">
        <Setter Property="Focusable" Value="false"/>
        <Setter Property="SnapsToDevicePixels" Value="true"/>
        <Setter Property="OverridesDefaultStyle" Value="true"/>
        <Setter Property="Height" Value="20"/>
        <Setter Property="Width" Value="30"/>
        <Setter Property="Cursor" Value="Hand"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type Thumb}">
                    <Canvas SnapsToDevicePixels="true">
                        <Grid Height="20" Width="30">
                            <Rectangle x:Name="Background"
                            Fill="{StaticResource CustomSliderThumBrush}" Stroke="#FFDADADA"
                            Height="20" Width="30"
                            RadiusX="3" RadiusY="3"/>
                            <TextBlock HorizontalAlignment="Center" VerticalAlignment="Center"
                            Foreground="White" FontSize="10"
                            Text="{Binding Value, RelativeSource={RelativeSource AncestorType={x:Type Slider}}}"/>
                        </Grid>
                    </Canvas>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsMouseOver" Value="true">
                            <Setter Property="Fill" TargetName="Background" Value="Orange"/>
                        </Trigger>
                        <Trigger Property="IsDragging" Value="true">
                            <Setter Property="Fill" TargetName="Background" Value="{StaticResource CustomSliderThumBrush}"/>
                        </Trigger>
                        <Trigger Property="IsEnabled" Value="false">
                            <Setter Property="Fill" TargetName="Background"  Value="Gray"/>
                        </Trigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>

    <ControlTemplate x:Key="CustomSliderControlTemplate" TargetType="{x:Type Slider}">
        <Border Background="Transparent" SnapsToDevicePixels="True">
            <Grid>
                <Grid.RowDefinitions>
                    <RowDefinition Height="{TemplateBinding MinHeight}" />
                </Grid.RowDefinitions>

                <DockPanel LastChildFill="True">
                    <Border x:Name="PART_SelectionRange" Height="5" ClipToBounds="True" Visibility="Visible">
                        <Rectangle Margin="0 0 -10 0" RadiusX="2" RadiusY="2" Fill="{StaticResource CustomSliderForegroundBrush}" />
                    </Border>
                    <Border ClipToBounds="True" Height="5" Visibility="Visible">
                        <Rectangle Margin="0 0 0 0" RadiusX="2" RadiusY="2" Fill="{StaticResource CustomSliderBackgroundSolidColorBrush}" />
                    </Border>
                </DockPanel>

                <Track x:Name="PART_Track">
                    <Track.Thumb>
                        <Thumb Style="{StaticResource CustomSliderThumbStyle}" VerticalAlignment="Center"
                            Width="{TemplateBinding MinWidth}" Height="{TemplateBinding MinHeight}" OverridesDefaultStyle="True" Focusable="False" />
                    </Track.Thumb>
                </Track>
            </Grid>
        </Border>
    </ControlTemplate>

    <Style  TargetType="{x:Type Slider}" x:Key="sliderStil">
        <Setter Property="Template" Value="{StaticResource CustomSliderControlTemplate}" />
        <Setter Property="VerticalAlignment" Value="Center" />
        <Setter Property="MinWidth" Value="30" />
        <Setter Property="MinHeight" Value="20" />
        <Setter Property="Height" Value="20" />
        <Setter Property="MaxHeight" Value="20" />
        <Setter Property="BorderBrush" Value="Transparent" />
        <Setter Property="Background" Value="Transparent" />
        <Setter Property="AutoToolTipPlacement" Value="None" />
        <Setter Property="IsMoveToPointEnabled" Value="True" />
        <Setter Property="SelectionStart" Value="0" />
        <Setter Property="SelectionEnd" Value="{Binding Path=Value, RelativeSource={RelativeSource Self}}" />
        <Setter Property="Stylus.IsPressAndHoldEnabled" Value="false" />
    </Style>

    <Style TargetType="Label" x:Key="labelStil" >
        <Setter Property="HorizontalContentAlignment" Value="Center"/>
        <Setter Property="VerticalContentAlignment" Value="Center"/>
        <Setter Property="FontWeight" Value="Bold"/>
        <Setter Property="FontSize" Value="15"/>
        <Setter Property="Foreground" Value="DarkSlateGray"/>
        <Setter Property="BorderThickness" Value="2"/>
        <Setter Property="BorderBrush" Value="LightBlue"/>
        <Setter Property="Background" Value="LightCyan"/>
        <Setter Property="Margin" Value="3"/>
        <Style.Resources>
            <Style TargetType="Border">
                <Setter Property="CornerRadius" Value="15 15 0 0" />
            </Style>
        </Style.Resources>
    </Style>

    <Style TargetType="TextBox" x:Key="textBoxStil" >
        <Setter Property="Margin" Value="3"/>
        <Setter Property="BorderThickness" Value="2"/>
        <Setter Property="BorderBrush" Value="LightBlue"/>
        <Setter Property="Background" Value="LightGoldenrodYellow"/>
        <Setter Property="VerticalContentAlignment" Value="Center"/>
        <Setter Property="HorizontalContentAlignment" Value="Center"/>
        <Setter Property="FontSize" Value="15"/>
        <Setter Property="FontWeight" Value="Bold"/>
        <Setter Property="Height" Value="30"/>
        <Style.Resources>
            <Style TargetType="Border">
                <Setter Property="CornerRadius" Value="0 0 15 15" />
            </Style>
        </Style.Resources>
        <Style.Triggers>
            <EventTrigger RoutedEvent="GotFocus">
                <BeginStoryboard>
                    <Storyboard>
                        <ColorAnimation 
                                Storyboard.TargetProperty="Background.Color"
                                To="LightPink" Duration="0:0:0.25"/>
                    </Storyboard>
                </BeginStoryboard>
            </EventTrigger>

            <EventTrigger RoutedEvent="LostFocus">
                <BeginStoryboard>
                    <Storyboard>
                        <ColorAnimation 
                                Storyboard.TargetProperty="Background.Color"
                                To="LightGoldenrodYellow" Duration="0:0:0.25"/>
                    </Storyboard>
                </BeginStoryboard>
            </EventTrigger>
        </Style.Triggers>
    </Style>
    <Style TargetType="ListBox" x:Key="listBoxStil" >
        <Setter Property="Margin" Value="3"/>
        <Setter Property="BorderThickness" Value="2"/>
        <Setter Property="BorderBrush" Value="LightBlue"/>
        <Setter Property="Foreground" Value="DarkSlateGray"/>
        <Setter Property="FontSize" Value="14"/>
        <Setter Property="FontWeight" Value="Bold"/>
        <Style.Resources>
            <Style TargetType="Border">
                <Setter Property="CornerRadius" Value="10 10 10 10" />
            </Style>
        </Style.Resources>
    </Style>

    <Style TargetType="Border" x:Key="BorderStil">
        <Setter Property="Margin" Value="10"/>
        <Setter Property="BorderThickness" Value="2"/>
        <Setter Property="BorderBrush" Value="LightBlue"/>
        <Setter Property="CornerRadius" Value="10"/>
    </Style>

</ResourceDictionary>
```

</td>
</tr>
</table>
