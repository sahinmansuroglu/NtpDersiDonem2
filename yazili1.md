## 2. Dönem 1. Yazılı ##

[Uygulamanın Tamamlanmış Halini indirmek için tıklayınız..](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8354576/2.Donem1.Yazili.zip)


### Uygulamanın Ekran Görüntüsü ###

![image](https://user-images.githubusercontent.com/28144917/160221900-74e9b6be-4b10-43b1-a233-e114ccdc8b35.png)

### Uygulamanın Dosya Yapısı ###

![image](https://user-images.githubusercontent.com/28144917/160222019-06a52788-adec-4fbb-ac34-e3f8e2d6ad03.png)

### Ogrenci Sınıfı (Ogrenci.cs) ###

```csharp
using System;
using System.Collections.Generic;
using System.Collections.ObjectModel;
using System.ComponentModel;
using System.Text;

namespace WpfApp40
{



    class Ogrenci : INotifyPropertyChanged
    {
        private string ad;
        public string Ad
        {
            get
            {
                return ad;
            }
            set
            {
                ad = value;
                OnPropertyChanged("Ad");
            }

        }
        private string soyad;
        public string Soyad
        {
            get
            {
                return soyad;
            }
            set
            {
                soyad = value;
                OnPropertyChanged("Soyad");
            }

        }

        private int? yazili1;
        public int? Yazili1
        {
            get { return yazili1; }
            set { 
                yazili1 = value;
                OnPropertyChanged("Yazili1");
                OnPropertyChanged("Ortalama");
                OnPropertyChanged("Durum");
            }
        }
        private int? okulNo;
        public int? OkulNo
        {
            get
            {
                return okulNo;
            }
            set
            {
                okulNo = value;
                OnPropertyChanged("OkulNo");
            }

        }
        private int? yazili2;

        public int? Yazili2
        {
            get { return yazili2; }
            set { 
                yazili2 = value;
                OnPropertyChanged("Yazili2");
                OnPropertyChanged("Ortalama");
                OnPropertyChanged("Durum");
            }
        }

        public double? Ortalama { 
            get {
                return (Yazili1 + Yazili2) / 2.0;
            } 
        
        }
        public string Durum
        {
            get
            {
                return Ortalama<50?"Kaldınız":"Geçtiniz";
            }

        }
        protected internal virtual void OnPropertyChanged(string propertyName)
        {
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
        }

        public event PropertyChangedEventHandler PropertyChanged;
    }
}

```

### Veri Dogrulama Sınıfı (OgrenciDogrulama.cs) ###

```csharp
using FluentValidation;
using System;
using System.Collections.Generic;
using System.Text;

namespace WpfApp40.Dogrulama
{
    class OgrenciDogrulama: AbstractValidator<Ogrenci>
    {
        public OgrenciDogrulama()
        {
            RuleFor(x => x.Ad).NotEmpty().WithMessage("Öğrenci Adı Gereklidir.");
            RuleFor(x => x.Ad).MinimumLength(3).WithMessage("Öğrenci Adı En az 3 karakter olmalı");
            RuleFor(x => x.Soyad).NotEmpty().WithMessage("Öğrenci Soyadı Gereklidir.");
            RuleFor(x => x.Soyad).MinimumLength(3).WithMessage("Öğrenci Soyadı En az 2 karakter olmalı");
            RuleFor(x => x.OkulNo).NotEmpty().WithMessage("Okul No Gereklidir");
            RuleFor(x => x.OkulNo).InclusiveBetween(1, 9999).WithMessage("Okul No En fazla 4 Rakamlı olmalı");
            RuleFor(x => x.Yazili1).NotEmpty().WithMessage("1. Yazılı Gereklidir");
            RuleFor(x => x.Yazili2).NotEmpty().WithMessage("2. Yazılı Gereklidir");
            RuleFor(x => x.Yazili1).InclusiveBetween(0, 100).WithMessage("1. Yazılı 0-100 arası olmalı");
            RuleFor(x => x.Yazili2).InclusiveBetween(0,100).WithMessage("2. Yazılı 0-100 arası olmalı");
        }
    }
}

```

### WPF Arayüzünün arka planında çalışan C# kodları (MainWindow.xaml.cs) ###

```csharp
using FluentValidation.Results;
using System;
using System.Collections.Generic;
using System.Collections.ObjectModel;
using System.ComponentModel;
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
using WpfApp40.Dogrulama;
using ValidationResult = FluentValidation.Results.ValidationResult;

namespace WpfApp40
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    /// 
    public partial class MainWindow : Window
    {
        ObservableCollection<Ogrenci> ogrenciList = new ObservableCollection<Ogrenci>();
       
        public MainWindow()
        {
            InitializeComponent();
            ogrenciList.Add(new Ogrenci
            {
                Ad = "Ezgi",
                Soyad = "EREN",
                Yazili1 = 95,
                Yazili2 = 85,
                OkulNo = 70,
            });
            ogrenciList.Add(new Ogrenci
            {
                Ad = "Ahmet",  
                Soyad = "DENİZ",
                Yazili1 = 45,
                Yazili2 = 30,
                OkulNo=80,
            });
            dtGrid1.ItemsSource = ogrenciList;
        }

        private void btnEkle_Click(object sender, RoutedEventArgs e)
        {

            HataList.Items.Clear();
            Ogrenci ogrenci = new Ogrenci
            {
                Ad = txtAd.Text,
                Soyad = txtSoyad.Text,
                Yazili1 = (Int32.TryParse(txtYazili1.Text, out int yazili1) ? yazili1 : (int?) null),
                Yazili2 = (Int32.TryParse(txtYazili2.Text, out int yazili2) ? yazili2 : (int?) null),
                OkulNo = (Int32.TryParse(txtOkulNo.Text, out int okulNo) ? okulNo : (int?)null)
            };

            OgrenciDogrulama dogrulama = new OgrenciDogrulama();
            ValidationResult dogrulamaSonucu = dogrulama.Validate(ogrenci);
            if (dogrulamaSonucu.IsValid == false)
            {
                foreach (ValidationFailure failure in dogrulamaSonucu.Errors)
                {
                    HataList.Items.Add(failure.ErrorMessage);
                }
            }
            else
            {
                Ogrenci bulunanOgrenci = ogrenciList.FirstOrDefault(x => x.OkulNo == Convert.ToInt32(txtOkulNo.Text));

                if (bulunanOgrenci == null)
                {
                    ogrenciList.Add(ogrenci);
                    textKutulariniTemizle();
                    MessageBox.Show("Yeni Öğrenci Ekleme Başarılı","Bilgi Penceresi",MessageBoxButton.OK,MessageBoxImage.Information); ;
                }
                else
                {
                    HataList.Items.Add("Girilen Öğrenci No daha önce kaydedildi....");
                }
            }
        }

        void textKutulariniTemizle()
        {
            txtAd.Clear();
            txtSoyad.Clear();
            txtYazili1.Clear();
            txtYazili2.Clear();
            txtOkulNo.Clear();
            HataList.Items.Clear();
        }

        private void btnSil_Click(object sender, RoutedEventArgs e)
        {

            if (dtGrid1.SelectedItem == null)
            {
                MessageBox.Show("Lütfen Bir Oğrenci Seçiniz.");
            }
            else
            {
                Ogrenci silinecekPersonel = (Ogrenci)dtGrid1.SelectedItem;
                MessageBoxResult cevap = MessageBox.Show("Kaydı Silmek İstediğinizden Emin Misiniz",
                            "Silme Onayı",
                            MessageBoxButton.YesNo,
                            MessageBoxImage.Question);

                if (cevap==MessageBoxResult.Yes)
                {
                    ogrenciList.Remove(silinecekPersonel);
                    textKutulariniTemizle();
                }
            }
        }

        private void dtGrid1_SelectionChanged(object sender, SelectionChangedEventArgs e)
        {
            if (dtGrid1.SelectedItem != null)
            {
                Ogrenci seciliOgrenci = (Ogrenci)dtGrid1.SelectedItem;
                txtAd.Text = seciliOgrenci.Ad;
                txtSoyad.Text = seciliOgrenci.Soyad;
                txtOkulNo.Text = seciliOgrenci.OkulNo.ToString();
                txtYazili1.Text = seciliOgrenci.Yazili1.ToString();
                txtYazili2.Text = seciliOgrenci.Yazili2.ToString();
            }
        }

        private void btnGuncelle_Click(object sender, RoutedEventArgs e)
        {
            if (dtGrid1.SelectedItem == null)
            {
                MessageBox.Show("Lütfen Güncellenecek Oğrenciyi Seçiniz.");
            }
            else
            {
                HataList.Items.Clear();
                Ogrenci guncellenecekOgrenci = new Ogrenci
                {
                    Ad = txtAd.Text,
                    Soyad = txtSoyad.Text,
                    Yazili1 = (Int32.TryParse(txtYazili1.Text, out int yazili1) ? yazili1 : (int?)null),
                    Yazili2 = (Int32.TryParse(txtYazili2.Text, out int yazili2) ? yazili2 : (int?)null),
                    OkulNo = (Int32.TryParse(txtOkulNo.Text, out int okulNo) ? okulNo : (int?)null)
                };

                OgrenciDogrulama dogrulama = new OgrenciDogrulama();
                ValidationResult dogrulamaSonucu = dogrulama.Validate(guncellenecekOgrenci);
                if (dogrulamaSonucu.IsValid == false)
                {
                    foreach (ValidationFailure failure in dogrulamaSonucu.Errors)
                    {
                        HataList.Items.Add(failure.ErrorMessage);
                    }
                }
                else
                {
                    MessageBoxResult cevap = MessageBox.Show("Güncellemek İstediğinizden Emin Misiniz",
                            "Güncelleme Onayı",
                            MessageBoxButton.YesNo,
                            MessageBoxImage.Question);

                    if (cevap == MessageBoxResult.Yes)
                    {
                        int? bulunanOgrenciNo = ((Ogrenci)dtGrid1.SelectedItem).OkulNo;
                        Ogrenci bulunanOgrenci = ogrenciList.FirstOrDefault(x => x.OkulNo == bulunanOgrenciNo);
                        bulunanOgrenci.Ad = txtAd.Text;
                        bulunanOgrenci.Soyad = txtSoyad.Text;
                        bulunanOgrenci.OkulNo = Convert.ToInt32(txtOkulNo.Text);
                        bulunanOgrenci.Yazili1 = Convert.ToInt32(txtYazili1.Text);
                        bulunanOgrenci.Yazili2 = Convert.ToInt32(txtYazili2.Text);
                        textKutulariniTemizle();
                        MessageBox.Show("Güncelleme Başarılı");
                    }
                 }
            }
        }

        private void btnTemizle_Click(object sender, RoutedEventArgs e)
        {
            textKutulariniTemizle();
        }

        private void btnYazdir_Click(object sender, RoutedEventArgs e)
        {
            PrintDialog printDialog = new PrintDialog();
            if (printDialog.ShowDialog() == true)
            {
                printDialog.PrintVisual(AnaPanel, "Veriler Yazdırılıyor");
            }
        }
    }
    }


```

### WPF Arayüzünün XAML kodları (MainWindow.xaml) ###

```xaml
<Window x:Class="WpfApp40.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp40"
        mc:Ignorable="d"
        Title="MainWindow" Height="700" Width="650"
        xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
        TextElement.Foreground="{DynamicResource MaterialDesignBody}"
        TextElement.FontWeight="Regular"
        TextElement.FontSize="15"
         TextOptions.TextFormattingMode="Ideal"
        TextOptions.TextRenderingMode="Auto"
        Background="{DynamicResource MaterialDesignPaper}"
        FontFamily="{DynamicResource MaterialDesignFont}">
   
    <DockPanel x:Name="AnaPanel">
        <ToolBarTray DockPanel.Dock="Top" Margin="5">
            <ToolBar  >
                <Button x:Name="btnEkle"  ToolTip="Öğrenci Ekle" Click="btnEkle_Click" Padding="4"   >
                    <materialDesign:PackIcon Height="30" Width="30" Kind="AccountMultiplePlus" />
                </Button>
                <Separator/>
                <Button x:Name="btnSil"  ToolTip="Öğrenci Sil"  Padding="4" Click="btnSil_Click"      >
                    <materialDesign:PackIcon Height="30" Width="30" Kind="Delete" />
                </Button>
                <Separator/>
                <Button x:Name="btnGuncelle"   ToolTip="Öğrenci Güncelle" Padding="4" Click="btnGuncelle_Click" >
                    <materialDesign:PackIcon Kind="Update" Height="30" Width="30" />
                </Button>
                <Separator/>

                <Button x:Name="btnTemizle"  ToolTip="Text Kutularını Temizle" Padding="4" Click="btnTemizle_Click"  >
                    <materialDesign:PackIcon Kind="Eraser" Height="30" Width="30" />
                </Button>
                <Separator/>

                <Button x:Name="btnYazdir"  ToolTip="Öğrenci Listesini Yazdır" Padding="4"  Click="btnYazdir_Click"  >
                    <materialDesign:PackIcon Kind="Printer" Height="30" Width="30"/>
                </Button>
                <Separator/>
                
            </ToolBar>
        </ToolBarTray>
        <StatusBar Name="sbar"  DockPanel.Dock="Bottom"       Background="WhiteSmoke" >

            <StatusBarItem HorizontalAlignment="Right">
                <TextBlock FontSize="13"  Name="tbCursorPozisyon">İşlem Yapılan Öğrenci : </TextBlock>
            </StatusBarItem>
            
            <StatusBarItem HorizontalAlignment="Left">
                <TextBlock Text="{Binding ElementName=txtAd, Path=Text}"  />
            </StatusBarItem>
            
            <StatusBarItem HorizontalAlignment="Left">
                <TextBlock Text="{Binding ElementName=txtSoyad, Path=Text}" Width="250" />
            </StatusBarItem>
            
            <Separator />
            
            <StatusBarItem >
                <TextBlock FontSize="13"  >Kayıtlı Öğrenci Sayısı:</TextBlock>
            </StatusBarItem>
            
            <StatusBarItem > 
                <TextBlock FontSize="13" Text="{Binding ElementName=dtGrid1, Path=Items.Count}" />
            </StatusBarItem>
            
        </StatusBar>
        
        <DataGrid x:Name="dtGrid1" SelectionChanged="dtGrid1_SelectionChanged" Height="200" Margin="5" DockPanel.Dock="Bottom" IsReadOnly="True" AutoGenerateColumns="False" >
            <DataGrid.Columns>
                <DataGridTextColumn Header="Okul No" 
                                    Binding="{Binding OkulNo}"/>
                <DataGridTextColumn Header="Öğrenci Adı" 
                                    Binding="{Binding Ad}"/>
                <DataGridTextColumn Header="Öğrenci Soyadı" 
                                    Binding="{Binding Soyad}"/>
                <DataGridTextColumn Header="1. Yazılı" 
                                    Binding="{Binding Yazili1}"/>
                <DataGridTextColumn Header="2. Yazılı" 
                                    Binding="{Binding Yazili2}"/>
                <DataGridTextColumn Header="Ortalama" 
                                    Binding="{Binding Ortalama}"/>
                <DataGridTextColumn Header="Durum" 
                                    Binding="{Binding Durum}"/>
            </DataGrid.Columns>
        </DataGrid>
      

        <GroupBox   Width="250"
                    DockPanel.Dock="Left"
                    Header="Öğrenci Bilgileri"
                    Margin="5">
            <StackPanel  Margin="5"  >
                <Label Content="Ad " Margin="0 0 0 -4" />
                <TextBox Name="txtAd" />
                <Label Content="Soyad " Margin="0 10 0 -4" />
                <TextBox Name="txtSoyad" />
                <Label Content="Okul No " Margin="0 10 0 -4" />
                <TextBox Name="txtOkulNo" />
                <Label Content="1. Yazılı " Margin="0 10 0 -4"   />
                <TextBox  x:Name="txtYazili1" Cursor="Arrow" />
                <Label Content="2. Yazılı " Margin="0 10 0 -4"  />
                <TextBox  x:Name="txtYazili2" />
            </StackPanel>
        </GroupBox>
        
        
            <GroupBox   DockPanel.Dock="Right"
                        Header="Hata Listesi"
                        Margin="5">
        
                        <ListBox x:Name="HataList" Foreground="red" FontWeight="Bold"/>
                
            </GroupBox>
      
        
    </DockPanel>
    
       
        
    
    
</Window>

```
