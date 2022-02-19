##  Quiz Sorusu ##


| Ekran Görüntüsü |Arayüzün Basit Anahat Yapısı|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/154793185-33549936-0cef-44e8-8137-872ac84c7472.png)|![image](https://user-images.githubusercontent.com/28144917/154793211-8f3ac023-961c-4c93-b3a0-61b82937f81f.png)|


[Uygulamanın Tamamlanmış Hali için tıklayınız](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8101714/WpfApp3.zip)

> **Görselleri Verilen Uygulamın arayüzünü Grid yapısını kullanarak tasarılayınız.(20 Puan)**

> **Listbox'a öğrenci ekletebilmek ve listbox'dan Öğrenci silebilmek için gerekli kodları yazınız.(20 Puan)**

![image](https://user-images.githubusercontent.com/28144917/154793357-3e0050b8-2e8a-480c-8bc8-7956d9283ec3.png)


### Çözümün XAML kodları ###

```xaml

<Window x:Class="WpfApp3.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp3"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="600">
    <Border Margin="10" BorderThickness="2" BorderBrush="LightBlue" CornerRadius="10">
    <Grid Margin="20">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="1*"/>
            <ColumnDefinition Width="1*" />
            <ColumnDefinition Width="1*"/>
            <ColumnDefinition Width="1*" />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="40"/>
            <RowDefinition Height="40"/>
            <RowDefinition Height="60"/>
            <RowDefinition Height="40"/>
            <RowDefinition />
        </Grid.RowDefinitions>
        <Label Content="Ad :"
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Right"
               Grid.Row="0"
               Grid.Column="0"/>
        <Label Content="Soyad :"
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Right"
               Grid.Row="0"
               Grid.Column="2"/>
        <Label Content="Yas :"
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Right"
               Grid.Row="1"
               Grid.Column="0"/>
        <Label Content="Puanlar :"
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Right"
               Grid.Row="2"
               Grid.Column="0"/>
        <Label Content="Okul No :"
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Right"
               Grid.Row="1"
               Grid.Column="2"/>
        <TextBox x:Name="txtAd" Margin="5"
                 Grid.Row="0"
                 Grid.Column="1"
                
            />
        <TextBox x:Name="txtSoyad" Margin="5"
                 Grid.Row="0"
                 Grid.Column="3"
                
            />
        <TextBox x:Name="txtYas" Margin="5"
                 Grid.Row="1"
                 Grid.Column="1"
                
            />
        <TextBox x:Name="txtOkulNo"
            Margin="5"
                 Grid.Row="1"
                 Grid.Column="3"
            />
        <Border Grid.Column="1" Grid.Row="2" Grid.ColumnSpan="3" BorderBrush="LightBlue" BorderThickness="1" CornerRadius="3">
            <Grid >
                <Grid.ColumnDefinitions>
                    <ColumnDefinition/>
                    <ColumnDefinition/>
                    <ColumnDefinition/>
                    <ColumnDefinition/>
                </Grid.ColumnDefinitions>
                <Grid.RowDefinitions>
                    <RowDefinition/>
                    <RowDefinition/>
                </Grid.RowDefinitions>
                <Label Content="1. Yazılı:"
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Center"
               Grid.Row="0"
               Grid.Column="0"/>
                <Label Content="2. Yazılı"
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Center"
               Grid.Row="0"
               Grid.Column="1"/>
                <Label Content="1. Perf."
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Center"
               Grid.Row="0"
               Grid.Column="2"/>
                <Label Content="2. Perf."
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Center"
               Grid.Row="0"
               Grid.Column="3"/>
                <TextBox x:Name="txtYazili1"
                     Margin="5 0 5 5"
                 Grid.Row="1"
                 Grid.Column="0"
            />
                <TextBox x:Name="txtYazili2"
                     Margin="5 0 5 5"
                 Grid.Row="1"
                 Grid.Column="1"
            />
                <TextBox x:Name="txtPerf1"
                     Margin="5 0 5 5"
                 Grid.Row="1"
                 Grid.Column="2"
            />
                <TextBox x:Name="txtPerf2"
                    Margin="5 0 5 5"
                 Grid.Row="1"
                 Grid.Column="3"
            />
            </Grid>
        </Border>



            <Button Content="Ekle" 
                    x:Name="btnEkle"
                Margin="5"
                Grid.Column="0" Grid.Row="3"
                FontWeight="Bold"
                    Click="btnEkle_Click"   
               />

            <Button x:Name="btnSil"
            Content="Sil" 
                Margin="5"
                Grid.Column="1" Grid.Row="3"
                FontWeight="Bold"
                    Click="btnSil_Click"    
            
              
                 />
            <Button Content="Güncelle" 
                    x:Name="btnGuncelle"
                Margin="5"
                Grid.Column="3" Grid.Row="3"
                FontWeight="Bold"
               />
            <Button Content="Ara" 
                    x:Name="btnAra"
                Margin="5"
                Grid.Column="2" Grid.Row="3"
                FontWeight="Bold"
               />

            <Border Grid.Row="4"
                Grid.ColumnSpan="4"
                    BorderBrush="LightBlue" BorderThickness="1" CornerRadius="10" Margin="5">
                <ListBox
        
            Margin="5"
            BorderThickness="0"
            Grid.Column="0"
            
            Name="lstOgrenciler"
            />


            </Border>
        
    </Grid>
    </Border>
</Window>



```


### Ogrenci Class'i ###

```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace WpfApp3
{
    class Ogrenci
    {
        public string Ad { get; set; }
        public string Soyad { get; set; }
        public int Yas { get; set; }
        public int OkulNo { get; set; }
        public int Yazili1 { get; set; }
        public int Yazili2 { get; set; }
        public int Perf1 { get; set; }
        public int Perf2 { get; set; }
        public double Ort { 
            get {

                return (Yazili1 + Yazili2 + Perf1 + Perf2) / 4.0;
            } 
        }
        public override string ToString()
        {
            return $"{OkulNo} {Ad} {Soyad} : {Ort}";
        }
    }
}


```

### Çözümün C# kodları ###

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

namespace WpfApp3
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        ObservableCollection<Ogrenci> ogrenciler = new ObservableCollection<Ogrenci>();
        public MainWindow()
        {
            InitializeComponent();

            ogrenciler.Add(new Ogrenci
            {
                Ad = "Ali",
                Soyad = "KEK",
                Yas = 34,
                OkulNo = 75,
                Yazili1 = 56,
                Yazili2=45,
                Perf1=77,
                Perf2=87
            });
            ogrenciler.Add(new Ogrenci
            {
                Ad = "Arda",
                Soyad = "TEK",
                Yas = 34,
                OkulNo = 96,
                Yazili1 = 56,
                Yazili2 = 99,
                Perf1 = 66,
                Perf2 = 87
            });
            ogrenciler.Add(new Ogrenci
            {
                Ad = "Sezgin",
                Soyad = "SET",
                Yas = 34,
                OkulNo = 95,
                Yazili1 = 56,
                Yazili2 = 45,
                Perf1 = 99,
                Perf2 = 87
            });
            lstOgrenciler.ItemsSource = ogrenciler;
        }

        private void btnEkle_Click(object sender, RoutedEventArgs e)
        {
            Ogrenci yeniOgrenci = new Ogrenci {
                Ad = txtAd.Text,
                Soyad = txtSoyad.Text,
                Yas = Convert.ToInt32(txtYas.Text),
                OkulNo = Convert.ToInt32(txtOkulNo.Text),
                Yazili1 = Convert.ToInt32(txtYazili1.Text),
                Yazili2 = Convert.ToInt32(txtYazili2.Text),
                Perf1 = Convert.ToInt32(txtPerf1.Text),
                Perf2 = Convert.ToInt32(txtPerf2.Text)

            };

            ogrenciler.Add(yeniOgrenci);

            txtAd.Clear();
            txtSoyad.Clear();
            txtYas.Clear();
            txtOkulNo.Clear();
            txtYazili1.Clear();
            txtYazili2.Clear();
            txtPerf1.Clear();
            txtPerf2.Clear();

        }

        private void btnSil_Click(object sender, RoutedEventArgs e)
        {
             if (lstOgrenciler.SelectedItem==null)
            {
                MessageBox.Show("Lütfen Bir Oğrenci Seçiniz.");
            }
            else
            {
                Ogrenci silinecekPersonel =(Ogrenci)lstOgrenciler.SelectedItem;
                ogrenciler.Remove(silinecekPersonel);

            }
        }
    }
}


```
