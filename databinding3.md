## INotifyPropertyChanged Arayüzünün Kullanımı ##

> Bir nesnenin property'sinin değeri değiştiğinde bu değişikliğin kullanıcı arayüzüne yansıtılabilmesi arayüze bildirim yapılması gerekir. Bu bildirim için INotifyPropertyChanged arayüzü(Interface) kullanılır.

> Aşağıdaki örnekte  bir Ogrenci Class'ı tanımlanmıştır. Bu class INotifyPropertyChanged Arayüzünden türetilmiştir. Bu arayüz sayesinde oluşturulan OnPropertyChanged metodu ile değeri değişen property'lerin  WPF formuna bildirimi yapılmıştır.

>   "Ad" ve "Soyad" property'lerinin set metodlarına dikkat edersek değer ataması yapılırken   OnPropertyChanged("Ad") ve  OnPropertyChanged("soyad") kodları sayesinde WPF arayüzüne değerin değiştiği ile ilgili bildirim yapılmıştır.

```csharp

  class Ogrenci: INotifyPropertyChanged
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
                OnPropertyChanged("soyad");
            }
        }
     

        protected internal virtual void OnPropertyChanged(string propertyName)
        {
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
        }

        public event PropertyChangedEventHandler PropertyChanged;
    }
```


### Puan Ortalama INotifyPropertyChanged ###


[WpfApp40.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8223476/WpfApp40.zip)


![image](https://user-images.githubusercontent.com/28144917/157664857-82e6d6e9-2ea3-452b-af88-63f27efa1a32.png)

**Arayüz**

```xaml
<Window x:Class="WpfApp40.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp40"
        mc:Ignorable="d"
        Title="MainWindow" Height="400" Width="250">
    <Window.Resources>
        <Style TargetType="TextBox">
            <Setter Property="Margin" Value="2"/>
        </Style>
    </Window.Resources>
    <StackPanel Margin="10" Name="stck1">
        <Label Content="Ad " />
        <TextBox Name="txtAd" Text="{Binding Path=Ad}" />
        <Label Content="Soyad "  />

        <TextBox Name="txtSoyad" Text="{Binding Path=Soyad}" />

        <Label Content="1. Yazılı "  />

        <TextBox  Text="{Binding Path=Yazili1, UpdateSourceTrigger=PropertyChanged}" />
        
        <Label Content="2. Yazılı "  />

        <TextBox  Text="{Binding Path=Yazili2, UpdateSourceTrigger=PropertyChanged}" />
        
        <Label Content="Ortalama "  />

        <TextBox  Text="{Binding Path=Ortalama, Mode=OneWay}" IsEnabled="False" />
       
        <Label Content="Durum "  />

        <TextBox  Text="{Binding Path=Durum, Mode=OneWay}"  IsEnabled="False" />



    </StackPanel>
</Window>

```


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

```csharp
using System;
using System.Collections.Generic;
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

namespace WpfApp40
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {

        Ogrenci ogrenci;

        public MainWindow()
        {
            InitializeComponent();

            ogrenci = new Ogrenci
            {
                Ad = "Ayhan",
                Soyad = "ERKMEN",
                Yazili1=66,
                Yazili2=55

            };
           stck1.DataContext = ogrenci;
        }

        
    }

  

}

```
