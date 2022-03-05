## Quiz Sorusu ##
> [Uygulamanın Tamamlanmış Halini indirmek için Tıklayınız..](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8185503/WpfApp9.zip)

| Ekran Görüntüsü |Arayüzün Anahat Yapısı|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/156755894-638888bd-72bc-402c-b060-49a5c4ba8ef2.png)|![image](https://user-images.githubusercontent.com/28144917/156755984-17a2de19-2285-4a04-9799-db27904e71e4.png)|
> Yukarıda Ekran Görüntüsü verilen uygulamayı aşağıda istenilenlere göre tasarlayınız.


| Uygulamanın Çalışan Halinin Ekran Görüntüsü |
|:--------:|
|![image](https://user-images.githubusercontent.com/28144917/156755716-ba83467d-0d29-4e15-87a8-d3c7899a9aa0.png)|

<table>
<tr>
<th>
Kullanıcı Arayüzün XAML kodları
</th>
</tr>
      <tr>
                <td>
                  
                  
```xaml
<Window x:Class="WpfApp9.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp9"
        mc:Ignorable="d"
        Title="Öğrenci Kayıt Demo" Height="450" Width="470">


    <Window.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <ResourceDictionary Source="Dictionary1.xaml"/>
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>

    </Window.Resources>
    
    
    <Border Style="{StaticResource disBorderStil}">
        <Grid Margin="10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="1*"/>
                <ColumnDefinition Width="2*"/>
             </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition Height="40"/>
                <RowDefinition Height="40"/>
                <RowDefinition Height="40"/>
                <RowDefinition Height="40"/>
                <RowDefinition Height="40"/>
                <RowDefinition Height="1*"/>
            </Grid.RowDefinitions>

            <Label Content="Ad Soyad" 
                       Grid.Row="0" Grid.Column="0"
                       Style="{StaticResource labelStil}"/>
            
            <Label Content="Okul No" 
                   Grid.Row="1" Grid.Column="0"
                   Style="{StaticResource labelStil}"/>
            
            <Label Content="1. Yazılı" 
                   Grid.Row="2" Grid.Column="0"
                   Style="{StaticResource labelStil}"/>
            
            <Label Content="2. Yazılı" 
                   Grid.Row="3" Grid.Column="0"
                   Style="{StaticResource labelStil}"/>
            
            <TextBox x:Name="txtAdSoyad"
                     Grid.Row="0" Grid.Column="1" 
                     Style="{StaticResource textBoxStil}"/>
            
            <TextBox x:Name="txtOkulNo" 
                      Style="{StaticResource textBoxStil}"
                     Grid.Row="1" Grid.Column="1" />
            
            <TextBox x:Name="txtYazili1" 
                     Style="{StaticResource textBoxStil}"
                     Grid.Row="2" Grid.Column="1" />
            
            <TextBox x:Name="txtYazili2" 
                     Grid.Row="3" Grid.Column="1" 
                     Style="{StaticResource textBoxStil}"/>



            <StackPanel Orientation="Horizontal" Grid.Row="4" Grid.Column="0" Grid.ColumnSpan="2">
                
                <Button x:Name="btnEkle" Content="Ekle" 
                        Style="{StaticResource butonStil}"
                        Click="btnEkle_Click"/>
                
                <Button x:Name="btnSil" 
                        Content="Sil"
                        Style="{StaticResource butonStil}"
                        Click="btnSil_Click"/>
                
                <Button x:Name="btnAra" 
                        Content="Ara"
                        Style="{StaticResource butonStil}"
                        Click="btnAra_Click"/>
                
                <Button x:Name="btnGuncelle" 
                        Content="Guncelle"
                        Style="{StaticResource butonStil}"
                        Click="btnGuncelle_Click"/>
                  
                <Button x:Name="btnTumunuListele" 
                        Content="Tümünü Listele"
                        Style="{StaticResource butonStil}"
                       Click="btnTumunuListele_Click"/>
                  
                <Button x:Name="btnTemizle" 
                        Content="Temizle"
                        Style="{StaticResource butonStil}"
                        Click="btnTemizle_Click" />

            </StackPanel>

            <ListBox x:Name="lbOgrenciler"
                     Style="{StaticResource ListBoxStil}"
                     Grid.Column="0"
                     Grid.Row="5"
                     Grid.ColumnSpan="2"
                     SelectionChanged="lbOgrenciler_SelectionChanged"/>
 
        </Grid>

    </Border>
</Window>

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
      
    <Style TargetType="Border" x:Key="disBorderStil">
        <Setter Property="Margin" Value="10"/>
        <Setter Property="BorderThickness" Value="2"/>
        <Setter Property="BorderBrush" Value="LightBlue"/>
        <Setter Property="CornerRadius" Value="10"/>
    </Style>

    <Style TargetType="Label" x:Key="labelStil">
        <Setter Property="HorizontalContentAlignment" Value="Right"/>
        <Setter Property="VerticalContentAlignment" Value="Center"/>
        <Setter Property="FontWeight" Value="Bold"/>
        <Setter Property="FontSize" Value="15"/>
        <Setter Property="Foreground" Value="DarkSlateGray"/>
        <Setter Property="BorderThickness" Value="2"/>
        <Setter Property="BorderBrush" Value="LightBlue"/>
        <Setter Property="Background" Value="LightYellow"/>
        <Setter Property="Margin" Value="2"/>
        <Style.Resources>
            <Style TargetType="Border">
                <Setter Property="CornerRadius" Value="10 0 0 10" />
            </Style>
        </Style.Resources>
    </Style>

    <Style TargetType="TextBox" x:Key="textBoxStil">
        <Setter Property="Margin" Value="2"/>
        <Setter Property="BorderThickness" Value="2"/>
        <Setter Property="BorderBrush" Value="LightBlue"/>
        <Setter Property="Background" Value="LightGoldenrodYellow"/>
        <Setter Property="VerticalContentAlignment" Value="Center"/>
        <Setter Property="FontSize" Value="15"/>
        <Style.Resources>
            <Style TargetType="Border">
                <Setter Property="CornerRadius" Value="0 10 10 0" />
            </Style>
        </Style.Resources>
    </Style>

    <Style TargetType="Button" x:Key="butonStil">
        <Setter Property="FontWeight" Value="Bold"/>
        <Setter Property="Foreground" Value="DarkSlateGray"/>
        <Setter Property="Margin" Value="5"/>
        <Setter Property="Padding" Value="8 0 8 0"/>
        <Setter Property="BorderBrush" Value="LightBlue" />
        <Setter Property="BorderThickness" Value="2" />
        <Style.Resources>
            <Style TargetType="Border">
                <Setter Property="CornerRadius" Value="5" />
            </Style>
        </Style.Resources>
    </Style>

    <Style TargetType="ListBox" x:Key="ListBoxStil">
        <Setter Property="Margin" Value="3"/>
        <Setter Property="BorderThickness" Value="2"/>
        <Setter Property="BorderBrush" Value="LightBlue"/>
        <Setter Property="Foreground" Value="DarkSlateGray"/>
        <Setter Property="FontSize" Value="13"/>
        <Style.Resources>
            <Style TargetType="Border">
                <Setter Property="CornerRadius" Value="10 10 10 10" />
            </Style>
        </Style.Resources>
    </Style>
      
</ResourceDictionary>
```

</td>
</tr>
</table>



<table>
<tr>
<th>
Ogrenci sınıfının bulunduğu Ogrenci.cs dosyası
</th>
</tr>
<tr>
<td>

```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace WpfApp9
{
    class Ogrenci
    {
  
        
        public string AdSoyad { get; set; }
        public int Yazili1 { get; set; }
        public int OkulNo { get; set; }
        public int Yazili2 { get; set; }
        public double Ortalama
        {
            get
            {
                return (Yazili1+Yazili2) / 2.0;
            }
        }

        public String Durum
        {
            get
            {
                return Ortalama < 50 ? "Kaldı" : "Geçti";

            }
        }
        public override string ToString()
        {
            return $"{OkulNo} {AdSoyad} {Ortalama}:{Durum}";
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

namespace WpfApp9
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        ObservableCollection<Ogrenci> ogrenciler = new ObservableCollection<Ogrenci>();
        ObservableCollection<Ogrenci> geciciOgrenciListesi= new ObservableCollection<Ogrenci>();
        public MainWindow()
        {
            InitializeComponent();
            ogrenciler.Add(new Ogrenci
            {
                AdSoyad = "Ali EFE",
                OkulNo = 75,
                Yazili1 = 56,
                Yazili2 = 45,
            });

            InitializeComponent();
            ogrenciler.Add(new Ogrenci
            {
                AdSoyad = "Ayhan ERDEM",
                OkulNo = 66,
                Yazili1 = 78,
                Yazili2 = 66,
            });

            lbOgrenciler.ItemsSource = ogrenciler;

        }

        private void btnEkle_Click(object sender, RoutedEventArgs e)
        {
            Ogrenci yeniOgrenci = new Ogrenci
            {
                AdSoyad = txtAdSoyad.Text,
                OkulNo = Convert.ToInt32(txtOkulNo.Text),
                Yazili1 = Convert.ToInt32(txtYazili1.Text),
                Yazili2 = Convert.ToInt32(txtYazili2.Text),
            };

            Ogrenci bulunanOgrenci = ogrenciler.FirstOrDefault(x => x.OkulNo == Convert.ToInt32(txtOkulNo.Text));
            if (bulunanOgrenci == null)
            {
                        ogrenciler.Add(yeniOgrenci);
                        txtAdSoyad.Clear();
                        txtOkulNo.Clear();
                        txtYazili1.Clear();
                        txtYazili2.Clear();

            }
            else
            {
                MessageBox.Show("Girilen Öğrenci No daha önce kaydedildi....");
            }
            

        }

        private void btnSil_Click(object sender, RoutedEventArgs e)
        {
            if (lbOgrenciler.SelectedItem == null)
            {
                MessageBox.Show("Lütfen Bir Oğrenci Seçiniz.");
            }
            else
            {
                Ogrenci silinecekPersonel = (Ogrenci)lbOgrenciler.SelectedItem;
                ogrenciler.Remove(silinecekPersonel);
                txtAdSoyad.Clear();
                txtOkulNo.Clear();
                txtYazili1.Clear();
                txtYazili2.Clear();

            }
        }

        private void btnAra_Click(object sender, RoutedEventArgs e)
        {
            Ogrenci bulunanOgrenci = ogrenciler.First(x => x.OkulNo == Convert.ToInt32(txtOkulNo.Text));
            if (bulunanOgrenci==null)
            {
                MessageBox.Show("Girilen Okul No ya ait Öğrenci Bulunamadı");
            }
            else
            {
                geciciOgrenciListesi.Clear();
                geciciOgrenciListesi.Add(bulunanOgrenci);
                lbOgrenciler.ItemsSource = geciciOgrenciListesi;
            }
           
        }

        private void btnGuncelle_Click(object sender, RoutedEventArgs e)
        {
            if (lbOgrenciler.SelectedItem == null)
            {
                MessageBox.Show("Lütfen Güncellenecek Oğrenciyi Seçiniz.");
            }
            else
            {
                Ogrenci bulunanOgrenci = (Ogrenci)lbOgrenciler.SelectedItem;
                bulunanOgrenci.AdSoyad = txtAdSoyad.Text;
                bulunanOgrenci.OkulNo = Convert.ToInt32(txtOkulNo.Text);
                bulunanOgrenci.Yazili1 = Convert.ToInt32(txtYazili1.Text);
                bulunanOgrenci.Yazili2 = Convert.ToInt32(txtYazili2.Text);
                txtAdSoyad.Clear();
                txtOkulNo.Clear();
                txtYazili1.Clear();
                txtYazili2.Clear();
                MessageBox.Show("Güncelleme Başarılı");    
                lbOgrenciler.ItemsSource = geciciOgrenciListesi;
                lbOgrenciler.ItemsSource = ogrenciler;

            }
       
        }

        private void btnTumunuListele_Click(object sender, RoutedEventArgs e)
        {
            lbOgrenciler.ItemsSource = ogrenciler;
        }

        private void lbOgrenciler_SelectionChanged(object sender, SelectionChangedEventArgs e)
        {
            if (lbOgrenciler.SelectedItem != null)
            {
                Ogrenci seciliOgrenci = (Ogrenci)lbOgrenciler.SelectedItem;
                txtAdSoyad.Text = seciliOgrenci.AdSoyad;
                txtOkulNo.Text = seciliOgrenci.OkulNo.ToString();
                txtYazili1.Text = seciliOgrenci.Yazili1.ToString();
                txtYazili2.Text = seciliOgrenci.Yazili2.ToString();


            }
        }

        private void btnTemizle_Click(object sender, RoutedEventArgs e)
        {
            txtAdSoyad.Clear();
            txtOkulNo.Clear();
            txtYazili1.Clear();
            txtYazili2.Clear();
        }
    }
}

```
      
      
</td>
</tr>
</table>
