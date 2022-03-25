## Veri Doğrulama ##

> Veri Doğrulama için [FluentValidation](https://fluentvalidation.net/) paketi kullanılmıştır.

> [Uygulamanın tamamlanmış Hali İçin Tıklayınız](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8348724/WpfApp40.zip)

> Uygulama Arayüzü

![image](https://user-images.githubusercontent.com/28144917/160082789-85867e7b-0dbb-4d07-9c41-c5900b672cfb.png)

> Uygulamanın klasör yapısı

![image](https://user-images.githubusercontent.com/28144917/160083234-dad73c63-1852-452c-87b3-ae751903d45c.png)


> Uygulamada kullanılan Ogrenci Sınıfı

```csharp
using System;
using System.Collections.Generic;
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

        private int yazili1;

        public int Yazili1
        {
            get { return yazili1; }
            set { 
                yazili1 = value;
                OnPropertyChanged("Ortalama");
                OnPropertyChanged("Durum");
            }
        }

        private int yazili2;

        public int Yazili2
        {
            get { return yazili2; }
            set { 
                yazili2 = value;
                OnPropertyChanged("Ortalama");
                OnPropertyChanged("Durum");

            }
        }

        public double Ortalama { 
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

> Veri Doğrulama Sınıfı (OgrenciDogrulama.cs)

```csharp
 class OgrenciDogrulama: AbstractValidator<Ogrenci>
    {
        public OgrenciDogrulama()
        {
            RuleFor(x => x.Ad).NotEmpty().WithMessage("Öğrenci Adı Gereklidir.");
            RuleFor(x => x.Ad).MinimumLength(3).WithMessage("Öğrenci Adı En az 3 karakter olmalı");
            RuleFor(x => x.Soyad).NotEmpty().WithMessage("Öğrenci Soyadı Gereklidir.");
            RuleFor(x => x.Soyad).MinimumLength(3).WithMessage("Öğrenci Soyadı En az 2 karakter olmalı");
            RuleFor(x => x.Yazili1).Must(Validate_Yazili).WithMessage("1. Yazılı 0-100 arası olmalı");
            RuleFor(x => x.Yazili2).Must(Validate_Yazili).WithMessage("2. Yazılı 0-100 arası olmalı");
        }

        private bool Validate_Yazili(int yazili)
        {
            if (yazili>100 || yazili < 0)
            {
                return false;
            }
            else
            {
                return true;
            }
        }

        
    }
```


> Uygulama arayüzünün arka planında çalışan C# kodları

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

        Ogrenci ogrenci;
        ObservableCollection<Ogrenci> ogrenciList = new ObservableCollection<Ogrenci>();
        public MainWindow()
        {
            InitializeComponent();
            dtGrid1.ItemsSource = ogrenciList;
            
           
        }

        private void button_Click(object sender, RoutedEventArgs e)
        {
            HataList.Items.Clear();
       

            if (!Int32.TryParse(txtYazili1.Text, out int yazili1)) {
                HataList.Items.Add("1. Yazılıyı Lütfen Rakam olarak Giriniz");
                return; 
            }
            if (!Int32.TryParse(txtYazili2.Text, out int yazili2))
            {
                HataList.Items.Add("2. Yazılıyı Lütfen Rakam olarak Giriniz");
                return;
            }
            ogrenci = new Ogrenci
            {
                Ad = txtAd.Text,
                Soyad = txtSoyad.Text,
                Yazili1 = yazili1,
                Yazili2 = yazili2

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
                ogrenciList.Add(ogrenci);
                txtAd.Clear();
                txtSoyad.Clear();
                txtYazili1.Clear();
                txtYazili2.Clear();

            }
            
           
        }

    }
    }
```

  



```
