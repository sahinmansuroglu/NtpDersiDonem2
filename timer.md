[Uygulamanın tamamlanmış hali için tıklayınız](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8130376/WpfApp4.zip)



![image](https://user-images.githubusercontent.com/28144917/155475615-4f3c0406-21e6-45e0-860a-09df8c9325b5.png)


``` xaml
<Window x:Class="WpfApp5.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp5"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <Grid Margin="10" Background="DarkBlue">
        <Grid.RowDefinitions>
            <RowDefinition Height="100"/>
            <RowDefinition Height="100*"/>
        </Grid.RowDefinitions>

        <StackPanel Grid.Row="0" Width="400" Orientation="Horizontal" >
            <Button  x:Name="btnBasla"
                Content="Başla" 
                    Padding="50 0 50 0"
                    FontSize="25"
                    Background="NavajoWhite"
                    Margin="10"
                     Click="btnBasla_Click" />
            <Button  x:Name="btSifirla"
                Content="Sıfırla" 
                    Padding="50 0 50 0"
                    FontSize="25"
                    Background="NavajoWhite"
                    Margin="10"
                     Click="btSifirla_Click"    />

        </StackPanel>
        <Label Content="0" Grid.Row="1" Foreground="Wheat"
               Name="lblSayac"
               Width="250"
               FontSize="150"
               BorderBrush="Wheat"
               BorderThickness="3"
               Margin="15"
               VerticalContentAlignment="Center"
               HorizontalContentAlignment="Center"/>
    </Grid>
</Window>

```

``` csharp
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

using System.Windows.Threading;

namespace WpfApp5
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {

        DispatcherTimer zamanlayici = new DispatcherTimer();
        public MainWindow()
        {
            InitializeComponent();
        }
        int sayac = 0;
        private void btnBasla_Click(object sender, RoutedEventArgs e)
        {
            sayac = 0;
            zamanlayici.Tick += Zamanlayici_Tick;
            zamanlayici.Interval = TimeSpan.FromSeconds(1);
            zamanlayici.Start();
        }

        private void Zamanlayici_Tick(object sender, EventArgs e)
        {
            sayac++;
            lblSayac.Content = sayac.ToString();
        }

        private void btSifirla_Click(object sender, RoutedEventArgs e)
        {
            zamanlayici.Stop();

            sayac = 0;
            lblSayac.Content = sayac.ToString();
        }
    }
}

```
