## DataContext Kullanımı ##

> Datacontext özelliği, verileri kullanıcı arayüzüne bağlamak için kullanılır.


<Window x:Class="WpfApp7.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp7"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="300">

    <Window.Resources>
        <Style TargetType="TextBox">
            <Setter Property="Margin" Value="5"/>
        </Style>
    </Window.Resources>
    

```xaml
    
    <StackPanel Margin="1" >
        
            <Label Content="Ad " />
            <TextBox Name="txtAd" Text="{Binding Path=Ad}" />
            <Label Content="Soyad " />
        <TextBox Name="txtSoyad" Text="{Binding Path=Soyad}" />


        <Button Click="Button_Click"  >
            Tıklayınız
        </Button>



    </StackPanel>
</Window>

```

```csharp

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

namespace WpfApp7
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {

        Ogrenci ogrenci = new Ogrenci
        {
            Ad = "arda",
            Soyad = "Aydın"
        };
        public MainWindow()
        {
            InitializeComponent();
            
            this.DataContext = ogrenci;    
            
        }

        private void TextBox_IsEnabledChanged(object sender, DependencyPropertyChangedEventArgs e)
        {

        }

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show($"{ogrenci.Ad} {ogrenci.Soyad}")
        }

       
    }
    class Ogrenci
    {
        public string Ad { get; set; }
        public string Soyad { get; set; }
    }

}
```
