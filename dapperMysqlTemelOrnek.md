### Kullanılan Veritabanı sql kodları ve workbench'deki tasarım  penceresi ###

```sql
CREATE TABLE `eokul`.`tblnot` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `ogrenciAdSoyad` VARCHAR(45) NOT NULL,
  `puan1` TINYINT(3) NOT NULL,
  `puan2` TINYINT(3) NOT NULL,
  `ortalama` DOUBLE NOT NULL,
  PRIMARY KEY (`id`));
```


![image](https://user-images.githubusercontent.com/28144917/166909704-b41ab263-4a34-4110-860d-a1694173e9ef.png)

### Kullanılan  Ogrenci Sınıfı ###

```csharp
 class Ogrenci
    {
        public int id { get; set; }
        public string ogrenciAdSoyad { get; set; }

        public int puan1 { get; set; }
        public int puan2 { get; set; }
        public double ortalama { get; set; }
        public override string ToString()
        {
            return $"{id}-{ogrenciAdSoyad}-{puan1}-{puan2}-{ortalama}";
        }
    }
    
```

### Uygulamanın Arayüzü ###

![image](https://user-images.githubusercontent.com/28144917/168019687-f0d05c91-4184-4480-8392-ce76cf3d2bd8.png)

### Uygulamanın Arayüzünün XAML Kodları ###

```xaml
<Window x:Class="VeritabaniUygulamaTamalandi.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:VeritabaniUygulamaTamalandi"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="900">
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
                <RowDefinition Height="40"/>
                <RowDefinition Height="1*"/>
            </Grid.RowDefinitions>

            <Label Content="Ad Soyad" 
                       Grid.Row="0" Grid.Column="0"
                       Style="{StaticResource labelStil}"/>

            <Label Content="Id" 
                   Grid.Row="1" Grid.Column="0"
                   Style="{StaticResource labelStil}"/>

            <Label Content="1. Yazılı" 
                   Grid.Row="2" Grid.Column="0"
                   Style="{StaticResource labelStil}"/>

            <Label Content="2. Yazılı" 
                   Grid.Row="3" Grid.Column="0"
                   Style="{StaticResource labelStil}"/>
            
            <Label Content="Ortalama" 
                   Grid.Row="4" Grid.Column="0"
                   Style="{StaticResource labelStil}"/>

            <TextBox x:Name="txtAdSoyad"
                     Grid.Row="0" Grid.Column="1" 
                     Style="{StaticResource textBoxStil}"/>

            <TextBox x:Name="txtId" 
                      Style="{StaticResource textBoxStil}"
                     Grid.Row="1" Grid.Column="1" IsEnabled="False" />

            <TextBox x:Name="txtYazili1" 
                     Style="{StaticResource textBoxStil}"
                     Grid.Row="2" Grid.Column="1" />

            <TextBox x:Name="txtYazili2" 
                     Grid.Row="3" Grid.Column="1" 
                     Style="{StaticResource textBoxStil}"/>
            <TextBox x:Name="txtOrtalama" 
                     Grid.Row="4" Grid.Column="1" 
                     Style="{StaticResource textBoxStil}"
                     IsEnabled="False"/>


            <StackPanel Orientation="Horizontal" Grid.Row="5" Grid.Column="0" Grid.ColumnSpan="2">

                <Button x:Name="btnEkle" Content="Ekle" 
                        Style="{StaticResource butonStil}" Click="btnEkle_Click"
                        />

                <Button x:Name="btnSil" 
                        Content="Sil"
                        Style="{StaticResource butonStil}" Click="btnSil_Click"
                        />

                <Button x:Name="btnAdSoyadaGoreAra" 
                        Content="Ad Soyada Göre Ara"
                        Style="{StaticResource butonStil}" Click="btnAdSoyadaGoreAra_Click"
                       />

                <Button x:Name="btnGecenOgrencileriListele" 
                        Content="Gecen Ogrencileri Listele"
                        Style="{StaticResource butonStil}" Click="btnGecenOgrencileriListele_Click" 
                       />
                <Button x:Name="btnKalanOgrencileriListele" 
                        Content="Kalan Ogrencileri Listele"
                        Style="{StaticResource butonStil}" Click="btnKalanOgrencileriListele_Click" 
                       />

                <Button x:Name="btnGuncelle" 
                        Content="Guncelle"
                        Style="{StaticResource butonStil}" Click="btnGuncelle_Click"
                      />

                <Button x:Name="btnTumunuListele" 
                        Content="Tümünü Listele"
                        Style="{StaticResource butonStil}"
                        Click="btnTumunuListele_Click"  
                       />

                <Button x:Name="btnTemizle" 
                        Content="Temizle"
                        Style="{StaticResource butonStil}" Click="btnTemizle_Click"
                       />

            </StackPanel>
            <DataGrid x:Name="dgOgrenciler"
                      Grid.Column="0"
                     Grid.Row="6"
                     Grid.ColumnSpan="2"
                      Margin="5"
                      SelectionChanged="dgOgrenciler_SelectionChanged"  />
           

        </Grid>

    </Border>
</Window>

```

### Stil yapılandırmalarının bulunduğu ResoruceDictionary Dosyası (Dictionary1.xaml) ###

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

### Uygulamanın Arka Plan Kodları (C#) ###

```csharp
using System;
using System.Collections.Generic;
using System.Data;
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
using Dapper;
using MySql.Data.MySqlClient;

namespace VeritabaniUygulamaTamalandi
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        string ConnectionString = "host=localhost;port=3306;user id=root;password=mtal2022;database=eokul;SslMode=None";
        public MainWindow()
        {
            InitializeComponent();
        }

        private void btnTumunuListele_Click(object sender, RoutedEventArgs e)
        {
            tumunuListele();   
        }

        void tumunuListele()
        {
            using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "select * from tblnot";

                var ogrenciler = baglanti.Query<Ogrenci>(sorgu).ToList();

                ogrenciler.ForEach(x => Console.WriteLine(x));
                Console.WriteLine("************************");
                ogrenciler.ForEach(x => Console.WriteLine(x.ogrenciAdSoyad));
                dgOgrenciler.ItemsSource = ogrenciler;

            }
        }

        void textKutulariniTemizle()
        {
            txtAdSoyad.Clear();
            txtYazili1.Clear();
            txtYazili2.Clear();
            txtOrtalama.Clear();
            txtId.Clear();

        }
        private void btnEkle_Click(object sender, RoutedEventArgs e)
        {
            //Aynı Ad soyad'a  sahip 2. kişi olmamalı

            using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "select * from tblnot where ogrenciAdSoyad=@ogrenciAdSoyad";

                var ogrenci = baglanti.QuerySingleOrDefault<Ogrenci>(sorgu,new { ogrenciAdSoyad =txtAdSoyad.Text});
                // Eğer Tabloda girilen AdSoyada ogrenci var ise "ogrenci" nesnesine atılır, yoksa null atılır

                if (ogrenci==null)
                {
                    Ogrenci yeniOgrenci = new Ogrenci
                    {
                        ogrenciAdSoyad = txtAdSoyad.Text,
                        puan1 = Int32.Parse(txtYazili1.Text),
                        puan2 = Int32.Parse(txtYazili2.Text)
                    };
                    yeniOgrenci.ortalama=(yeniOgrenci.puan1 + yeniOgrenci.puan2)/2.0;

                    
                    //burada ogrenci ekleme yapılır
                    sorgu = "Insert into tblnot(ogrenciAdSoyad,puan1,puan2,ortalama) values (@ogrenciAdSoyad,@puan1,@puan2,@ortalama)";

                    int eklenenSayi=baglanti.Execute(sorgu,yeniOgrenci);
                    if (eklenenSayi == 1)
                    {
                        textKutulariniTemizle();
                        tumunuListele();
                        MessageBox.Show("Yeni Öğrenci Ekleme Başarılı");

                    }
                    else
                    {
                        MessageBox.Show("Öğrenci Ekleme Başarısız");
                    }

                }
                else
                {
                    MessageBox.Show($"{txtAdSoyad.Text} ad soyadlı kişi zaten kayıtlı, lütfen farklı bir ad soyad giriniz");

                }

            }

         }

        private void btnTemizle_Click(object sender, RoutedEventArgs e)
        {
            textKutulariniTemizle();
        }

        private void btnSil_Click(object sender, RoutedEventArgs e)
        {
            if (dgOgrenciler.SelectedItem!=null)
            {
                using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
                {
                    string sorgu = "DELETE FROM tblnot WHERE id=@id";
                    int silinenKayıtSayisi = baglanti.Execute(sorgu, new { id = Int32.Parse(txtId.Text) });
                    MessageBox.Show($"{silinenKayıtSayisi} tane kayıt silinmiştir.");
                    textKutulariniTemizle();
                    tumunuListele();
                }
            }
            else
            {

                MessageBox.Show("Lütfen Silinecek Öğrenciyi Listeden Seçiniz");
            }
           
        }

        private void dgOgrenciler_SelectionChanged(object sender, SelectionChangedEventArgs e)
        {
            try
            {
                Ogrenci secilenOgrenci = (Ogrenci)dgOgrenciler.SelectedItem;

                if (secilenOgrenci != null)
                {
                    txtAdSoyad.Text = secilenOgrenci.ogrenciAdSoyad;
                    txtId.Text = secilenOgrenci.id.ToString();
                    txtOrtalama.Text = secilenOgrenci.ortalama.ToString();
                    txtYazili1.Text = secilenOgrenci.puan1.ToString();
                    txtYazili2.Text = secilenOgrenci.puan2.ToString();
                }

            }
            catch (Exception)
            {

              
            }
            
        }

        private void btnAdSoyadaGoreAra_Click(object sender, RoutedEventArgs e)
        {
            using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "select * from tblnot where ogrenciAdSoyad=@ogrenciAdSoyad ";

                var ogrenciler = baglanti.Query<Ogrenci>(sorgu,new { ogrenciAdSoyad =txtAdSoyad.Text}).ToList();
                if (ogrenciler.Count==0)
                {
                    MessageBox.Show("Aranalan Kayıt Bulunamadı");
                }
                else
                {
                    dgOgrenciler.ItemsSource = ogrenciler;
                }
              

            }
        }

        private void btnGecenOgrencileriListele_Click(object sender, RoutedEventArgs e)
        {
            using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "select * from tblnot where ortalama>=50";

                var ogrenciler = baglanti.Query<Ogrenci>(sorgu).ToList();
                if (ogrenciler.Count == 0)
                {
                    MessageBox.Show("Geçen Öğrenci Bulunmamaktadır.");
                }
                else
                {
                    dgOgrenciler.ItemsSource = ogrenciler;
                }


            }
        }

        private void btnKalanOgrencileriListele_Click(object sender, RoutedEventArgs e)
        {
            using(IDbConnection baglanti = new MySqlConnection(ConnectionString))
            {
                string sorgu = "select * from tblnot where ortalama<50";

                var ogrenciler = baglanti.Query<Ogrenci>(sorgu).ToList();
                if (ogrenciler.Count == 0)
                {
                    MessageBox.Show("Kalan Öğrenci Bulunmamaktadır.");
                }
                else
                {
                    dgOgrenciler.ItemsSource = ogrenciler;
                }


            }
        }

        private void btnGuncelle_Click(object sender, RoutedEventArgs e)
        {
            if (dgOgrenciler.SelectedItem != null)
            {
                Ogrenci guncellenecekOgrenci = new Ogrenci
                {
                    ogrenciAdSoyad = txtAdSoyad.Text,
                    puan1 = Int32.Parse(txtYazili1.Text),
                    puan2 = Int32.Parse(txtYazili2.Text),
                    id= Int32.Parse(txtId.Text),
                };
                guncellenecekOgrenci.ortalama = (guncellenecekOgrenci.puan1 + guncellenecekOgrenci.puan2) / 2.0;
               
                using (IDbConnection baglanti = new MySqlConnection(ConnectionString))
                {
                    string sorgu = "UPDATE tblnot set ogrenciAdSoyad=@ogrenciAdSoyad, puan1=@puan1, puan2=@puan2, ortalama=@ortalama WHERE id=@id";
                    int silinenKayıtSayisi = baglanti.Execute(sorgu,guncellenecekOgrenci);
                    MessageBox.Show($"{silinenKayıtSayisi} tane kayıt güncellenmiştir.");
                    textKutulariniTemizle();
                    tumunuListele();
                }
            }
            else
            {

                MessageBox.Show("Lütfen Güncellenecek Öğrenciyi Listeden Seçiniz");
            }
        }
    }
}

```

[Sınıf Ortamında Uygulama İçin Verilen Dökümanları İndirmek İçin Tıklayınız.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8676073/Sinif.Ortaminda.Uygulam.Icin.Verilen.Dokumanlar.zip)

[Uygulamanın tamamlanmış halini indirmek için Tıklayınız..](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8676077/VeritabaniUygulamaTamalandi.zip)

[Uygulamanın tamamlanmış halini indirmek için Tıklayınız.. (FluentValidation İle Doğrulama Yapılmış)](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8705971/VeritabaniProjesi.zip)
