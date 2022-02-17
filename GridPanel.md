## Grid Panel Kullanımı ##

> Grid Panel  kullanıcı arayüzünü satır ve sutunlara bölerek bir tablo oluşturur. Eklenmek istenilen UI nesneleri oluşturan tablonun istenilen hücrelerine eklenir. Hangi hücreye ekleneceğinin belirlenmesi için satir numarası ve sutun numarası belirtilir 

| Örnek Kod | Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/154025536-2b0c8332-4945-43e8-aa93-994228051224.png)|![image](https://user-images.githubusercontent.com/28144917/154025502-74756e1f-37ee-4de4-87ba-77576ebf7ec8.png)|
|![image](https://user-images.githubusercontent.com/28144917/154025708-0e39e53e-e39a-49dc-96a9-9366478fdabb.png)|![image](https://user-images.githubusercontent.com/28144917/154025664-384a6b92-7080-4734-98a8-62b562888fc9.png)|
|![image](https://user-images.githubusercontent.com/28144917/154025832-b33addd4-ea9d-49ed-9767-6d50f614716e.png)|![image](https://user-images.githubusercontent.com/28144917/154025877-2e027109-b2e9-4343-b3b6-ebf3a2340e3d.png)|
|![image](https://user-images.githubusercontent.com/28144917/154026189-2ac39b49-4e8a-4f42-8b79-4f80e3fb28ee.png)|![image](https://user-images.githubusercontent.com/28144917/154026234-f46d61dd-b57f-4df2-8e2c-ed848bcea0e9.png)|
|![image](https://user-images.githubusercontent.com/28144917/154026590-7ecdaed0-7aa4-4494-910b-cddde8d87dca.png)|![image](https://user-images.githubusercontent.com/28144917/154026512-0208b422-8f41-4cda-a3e1-deff2b8eb9f4.png)|
|![image](https://user-images.githubusercontent.com/28144917/154027005-12fd7e71-64d4-4a3b-b46e-58f95dabcef3.png)|![image](https://user-images.githubusercontent.com/28144917/154027025-0c376c84-1ab0-41a9-871d-d16b0bb7f1d3.png)|

## Grid Panel Kullanımı Örnek ##

| Ekran Görüntüsü - 1  | Ekran Görüntüsü - 2  |
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/154053374-a45dbf61-c578-4a46-b456-c2db34b7cbb6.png) | ![image](https://user-images.githubusercontent.com/28144917/154053458-52212080-d5c2-415c-a67b-ed9fab9fbdeb.png)|


**XAML kodları**
```xaml
<Window x:Class="WpfApp23.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp23"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="400">
    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="1*"/>
            <ColumnDefinition Width="2*" />
   
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="40"/>
            <RowDefinition Height="40"/>
            <RowDefinition Height="40"/>
            <RowDefinition Height="40"/>
            <RowDefinition />
        </Grid.RowDefinitions>
        <Label Content="AdSoyad :"
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Right"
               Grid.Row="0"
               Grid.Column="0"/>
        <Label Content="Yas :"
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Right"
               Grid.Row="1"
               Grid.Column="0"/>
        <Label Content="Cinsiyet :"
               FontWeight="Bold"
               FontSize="14"
               VerticalAlignment="Center"
               HorizontalAlignment="Right"
               Grid.Row="2"
               Grid.Column="0"/>
        <TextBox x:Name="txtAdSoyad" Margin="5"
                 Grid.Row="0"
                 Grid.Column="1"
                
            />
        <TextBox x:Name="txtYas"
            Margin="5"
                 Grid.Row="1"
                 Grid.Column="1"
            />

        <RadioButton Content="Bay" 
                     Grid.Column="1" Grid.Row="2"
                     HorizontalAlignment="Left"
                     FontSize="14"
                     FontWeight="Bold"
                     VerticalAlignment="Center"
                     Margin="20 0 0 0"
                     x:Name="rbBay"
                     VerticalContentAlignment="Center"/>
        
        <RadioButton Content="Bayan" 
                     Grid.Column="1" Grid.Row="2"
                     HorizontalAlignment="Right"
                      FontSize="14"
                     FontWeight="Bold"
                     VerticalAlignment="Center"
                     Margin="0 0 20 0"
                     VerticalContentAlignment="Center"/>

        <Button x:Name="btnSil"
            Content="Sil" 
                Margin="5"
                Grid.Column="0" Grid.Row="3"
                FontWeight="Bold"
                Click="btnSil_Click"
              
                 />
        <Button Content="Ekle" 
                Margin="5"
                Grid.Column="1" Grid.Row="3"
                FontWeight="Bold"
                Click="Button_Click"   />
        <ListBox
            BorderBrush="PaleVioletRed"
            Margin="5"
            BorderThickness="2"
            Grid.Column="0"
            Grid.Row="4"
            Grid.ColumnSpan="2"
            Name="lstPersonels"
            />

    </Grid>
</Window>


```

**Personel.cs (Personel Class'ı)**
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace WpfApp23
{
    class Personel
    {
        public string AdSoyad { get; set; }
        public int Yas { get; set; }
        public string Cinsiyet { get; set; }
        public override string ToString()
        {
            return $"{AdSoyad} {Yas} {Cinsiyet}";
        }
    }
}

```

**Ana Program**
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

namespace WpfApp23
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        ObservableCollection<Personel> personels = new ObservableCollection<Personel>();
        public MainWindow()
        {
            
            InitializeComponent();

            personels.Add(new Personel { AdSoyad = "Ali Er", Yas = 45, Cinsiyet = "Bay" });
            personels.Add(new Personel { AdSoyad = "Esra ESER", Yas = 34, Cinsiyet = "Bayan" });
            personels.Add(new Personel { AdSoyad = "Ekin KORKMAZ", Yas = 21, Cinsiyet = "Bayan" });
            lstPersonels.ItemsSource = personels;
        }

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            Personel yeniPersonel = new Personel
            {
                AdSoyad = txtAdSoyad.Text,
                Yas=Convert.ToInt32( txtYas.Text),
                Cinsiyet=rbBay.IsChecked==true?"Bay":"Bayan"
            };

            personels.Add(yeniPersonel);
             
        }

       

        private void btnSil_Click(object sender, RoutedEventArgs e)
        {
            if (lstPersonels.SelectedItem==null)
            {
                MessageBox.Show("Lütfen Bir Personel Seçiniz.");
            }
            else
            {
                Personel silinecekPersonel =(Personel) lstPersonels.SelectedItem;
                personels.Remove(silinecekPersonel);

            }
         
        }
    }
}

```
