## FluentValidation ile Veri Doğrulama ##

[FluentValidation](https://fluentvalidation.net/) kolay ve hizli bir şekilde veri doğrulama yapılmasına imkan sağlayan bir .NET kütüphanesidir.

> Bir nesne için doğrulama kuralı tanımlayabilmek için ilk olarak AbstractValidator<T> 'sınıfını miras alan  bir sınıf türetilmesi gerekir.
   
> Aşağıdaki gibi Bir Ogrenci Sınıfı için doğrulama kuralları oluşturalım.
   
 ```csharp
    class Ogrenci
    {
        public string AdSoyad { get; set; }
        public int? DogumYili { get; set; }
        public int? Puan { get; set; }

        public override string ToString()
        {
            return $"{AdSoyad} {DogumYili} {Puan}";
        }
    }
``` 
**Not:** int tipinde tanımlanan bir değişkene değer ataması yapılmazsa varsayılan değeri 0 dir. Eğer null değer alabilen bir  tipinde değişken tanımlanması istenirse int? veri tipi kullanılır. (float?, double?, short?, byte? gibi)
   
   
   
> Yukarıdaki sınıfa doğrulama kuralı tanımlamak için  AbstractValidator<Ogrenci> sınıfını miras alan bir sınıf tanımlanır.
    
```csharp
    using FluentValidation;
    class OgrenciDogrulama:AbstractValidator<Ogrenci>
    {
        
    }
```
    
> Doğrulama kuralları yukarıdaki sınıfın kurucu metodu içerisinde tanımlanır.
 
```csharp
using FluentValidation;
 class OgrenciDogrulama:AbstractValidator<Ogrenci>
    {
        public OgrenciDogrulama()
        {
            RuleFor(x => x.AdSoyad).NotEmpty().WithMessage("Öğrenci Adı ve Soyadı boş Geçilemez");
            RuleFor(x => x.AdSoyad).MinimumLength(6).WithMessage("Öğrenci Adı ve Soyadı  enaz 6 karakterden oluşmalı");
            RuleFor(x => x.DogumYili).NotNull().WithMessage("Dogum Yili Gerekli");
            RuleFor(x => x.DogumYili).InclusiveBetween(1910, DateTime.Now.Year).WithMessage("Doğum Yılı 1910 ile günümüz arasında olmalı");
            RuleFor(x => x.Puan).NotNull().WithMessage("Puan Gerekli");
            RuleFor(x => x.Puan).InclusiveBetween(0,100).WithMessage("Puan 0-100 arasında olmalı");
        }
    }
```
   
**Not:** [Fluentvalidation kütüphanesindeki yerleşik doğrulama kurallarını incelemek için tıklayınız](https://docs.fluentvalidation.net/en/latest/built-in-validators.html)
   
> Doğrulamayı Çalıştırmak için Validate Metodu kullanılır

```csharp
Ogrenci ogrenci = new Ogrenci()
            {
                AdSoyad = "Ali",
                DogumYili = 1935,
                Puan = 85
            };
OgrenciDogrulama dogrulama = new OgrenciDogrulama();
ValidationResult dogrulamaSonucu = dogrulama.Validate(ogrenci);
```    
> Validate methodu  ValidationResult nesnesi döndürür. Bu değer;
   
<ul>
   <li>Eğer <b>IsValid=True</b> ise doğrulamanın başarılı olduğu anlamına gelir.</li>
<li>Eğer <b>IsValid=False</b> ise hata vardır. Errors listesi ile hatalara erişilebilinir.</li>
</ul>

   
```csharp    
         if (dogrulamaSonucu.IsValid == false)
            {
                foreach (ValidationFailure herBirHata in dogrulamaSonucu.Errors)
                {
                    HataList.Items.Add(herBirHata.ErrorMessage);
                }
            }
            else
            {
                liste1.Items.Add(ogr);
                txtPuan.Clear();
                txtDogumYili.Clear();
                txtAdSoyad.Clear();
                MessageBox.Show("Herşey başarılı");

            }    
```
### Örnek ###
   
![image](https://user-images.githubusercontent.com/28144917/160344914-88c100bf-a090-4568-a3dd-f2d66282e7a4.png)

> Yukarıda kullanıcı arayüzü verilen uygulamada aşağıda belirtilen doğrulamalar yapıldıktan sonra Ad Soyad, Dogum Yılı ve Puanı bir metin içerisinde birleştirilerek listbox'a ekletilmiştir.(Aşağıdaki doğrulamalar FluentValidation kütüphanesi kullanılarak yapılmıştır.)
<ol>
<li>Öğrenci Ad Soyadı Boş Geçilirse "Lütfen Ad Soyad Giriniz" uyarısı verilecek</li>
<li>Öğrenci Ad Soyadı 6 Karakterden az ise ""Ad Soyad en az 6 karakterden olusmali"" uyarısı verilecek</li>
<li>Doğum Yılı boş geçilirse veya rakam dışında bir karakter girilirse "Doğum Tarihi girilmeli ve Rakam olmalı" uyarısı verilecek</li>
<li>Doğum Yılı 1910'dan Küçükse "Dogum yili 1910'dan Küçük olamaz" uyarısı verilecek</li>
<li>Doğum Yılı Güncel yıldan büyükse "Doğum yılı Bulunulan Yıldan Fazla olamaz" uyarısı verilecek</li>
<li>Puan boş geçilirse veya rakam dışında bir karakter girilirse "Puan girilmeli ve Rakam olmalı" uyarısı verilecek</li>
<li>Puan 0-100 arası değilse "Puan 0-100 arası olmalı" uyarısı verilecek</li>
</ol>   
   
   
**Dosya Yapısı**
   
![image](https://user-images.githubusercontent.com/28144917/160344949-8a94865c-a159-4b27-a637-80e2a82f93cd.png)


**Ogrenci Class'ı**
   
```csharp
class Ogrenci
    {
        public string AdSoyad { get; set; }
        public int? DogumYili { get; set; }
        public int? Puan { get; set; }

        public override string ToString()
        {
            return $"{AdSoyad} {DogumYili} {Puan}";
        }
    }
```

**OgrenciDogrulama Class'ı**   
   
```csharp

 class OgrenciDogrulama:AbstractValidator<Ogrenci>
    {
        public OgrenciDogrulama()
        {
            RuleFor(x => x.AdSoyad).NotEmpty().WithMessage("Öğrenci Adı ve Soyadı boş Geçilemez");
            RuleFor(x => x.AdSoyad).MinimumLength(6).WithMessage("Öğrenci Adı ve Soyadı  enaz 6 karakterden oluşmalı");
            RuleFor(x => x.DogumYili).NotNull().WithMessage("Dogum Yili Gerekli");
            RuleFor(x => x.DogumYili).InclusiveBetween(1910, DateTime.Now.Year).WithMessage("Doğum Yılı 1910 ile günümüz arasında olmalı");
            RuleFor(x => x.Puan).NotNull().WithMessage("Puan Gerekli");
            RuleFor(x => x.Puan).InclusiveBetween(0,100).WithMessage("Puan 0-100 arasında olmalı");
        }
    }
```

**Kullanıcı Arayüzünün arkaplanında çalışan kodlar**
   
```csharp
  
  using FluentValidation.Results;
using System;
using System.Collections.Generic;
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
using WpfApp58.Dogrulama;
using ValidationResult = FluentValidation.Results.ValidationResult;

namespace WpfApp58
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            HataList.Items.Clear();
            Ogrenci ogr = new Ogrenci()
            {
                AdSoyad = txtAdSoyad.Text,
                DogumYili = (Int32.TryParse(txtDogumYili.Text, out int dogumYili) ? dogumYili : (int?)null),
                Puan = (Int32.TryParse(txtPuan.Text, out int puan) ? puan : (int?)null)
            };

            OgrenciDogrulama dogrulama = new OgrenciDogrulama();
            ValidationResult dogrulamaSonucu = dogrulama.Validate(ogr);
            if (dogrulamaSonucu.IsValid == false)
            {
                foreach (ValidationFailure herBirHata in dogrulamaSonucu.Errors)
                {
                    HataList.Items.Add(herBirHata.ErrorMessage);
                }
            }
            else
            {
                liste1.Items.Add(ogr);
                txtPuan.Clear();
                txtDogumYili.Clear();
                txtAdSoyad.Clear();
                MessageBox.Show("Herşey başarılı");

            }
        }
    }
}

  
```

**Kullanıcı Arayüzünün XAML kodları**   
   
```xaml

<Window x:Class="WpfApp58.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp58"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="300">
    <StackPanel>
        <ListBox x:Name="HataList" Foreground="red" />
        <Label Content="Ad Soyad"/>
        <TextBox x:Name="txtAdSoyad"/>
        <Label Content="Dogum Yılı"/>
        <TextBox x:Name="txtDogumYili"/>
        <Label Content="Puanı"/>
        <TextBox x:Name="txtPuan"/>
        <Button Content="Listeye Ekle" Click="Button_Click"/>
        <ListBox x:Name="liste1"/>
    </StackPanel>
</Window>


```
