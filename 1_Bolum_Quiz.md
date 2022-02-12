##  Quiz Sorusu ##

[Proje Dosyası](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8053909/WpfApp1.zip)



![image](https://user-images.githubusercontent.com/28144917/153717856-e71ac89f-fa7f-49d9-9bec-202053aa166d.png)

![image](https://user-images.githubusercontent.com/28144917/153717906-6f5e18d5-7c1c-4bc0-b0b0-c6113c62afc1.png)


```xaml
<Window x:Class="WpfApp1.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp1"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="700" 
        WindowStyle="None"
        AllowsTransparency="True"
        Background="Transparent"
        >
    <Grid>
        <Border CornerRadius="25" Background="#FF8000FF" Padding="20">
            <Grid>
                <StackPanel Orientation="Horizontal" Height="40" VerticalAlignment="Top" Margin="10">
                    <Border CornerRadius="10,0,0,10" Background="White">
                        <Label Content="1. Sayı" VerticalContentAlignment="Center" Width="150" FontWeight="Bold" />
                    </Border>
                    <Border CornerRadius="0,10,10,0" Background="White" Padding="5">
                        <TextBox x:Name="txtSayi1" VerticalContentAlignment="Center" Width="150" />
                    </Border>

                    <Border CornerRadius="10,0,0,10" Background="White" Margin="20 0 0 0 ">
                        <Label Content="2. Sayı" VerticalContentAlignment="Center" Width="150" FontWeight="Bold"  />
                    </Border>
                    <Border CornerRadius="0,10,10,0" Background="White" Padding="5">
                        <TextBox x:Name="txtSayi2" VerticalContentAlignment="Center" Width="150" />
                    </Border>

                </StackPanel>

               

                <StackPanel Orientation="Horizontal" Height="40" VerticalAlignment="Top" Margin="10 70,0,0" HorizontalAlignment="Center">
                    <Border CornerRadius="10,10,10,10" Background="White" Width="70" Padding="5,0,0,0" Margin="20 0 0 0">
                        <RadioButton x:Name="rbTopla" GroupName="islem" Content="Topla" VerticalAlignment="Center" FontWeight="Bold" />
                    </Border>
                    <Border CornerRadius="10,10,10,10" Background="White" Width="70" Padding="5,0,0,0" Margin="20 0 0 0">
                        <RadioButton x:Name="rbCikart" GroupName="islem" Content="Çıkart" VerticalAlignment="Center" FontWeight="Bold" />
                    </Border>
                    <Border CornerRadius="10,10,10,10" Background="White" Width="70" Padding="5,0,0,0" Margin="20 0 0 0">
                        <RadioButton x:Name="rbCarp" GroupName="islem" Content="Çarp" VerticalAlignment="Center" FontWeight="Bold" />
                    </Border>
                    <Border CornerRadius="10,10,10,10" Background="White" Width="70" Padding="5,0,0,0" Margin="20 0 0 0">
                        <RadioButton x:Name="rbBol" GroupName="islem" Content="Böl" VerticalAlignment="Center" FontWeight="Bold" />
                    </Border>

                </StackPanel>

                <StackPanel Orientation="Horizontal"  Height="50" VerticalAlignment="Top" Margin="10 140,0,0" HorizontalAlignment="Center">
                    <Border CornerRadius="10,10,10,10" Background="#FF1A1123">
                        <Button x:Name="btnHesapla" Content="Hesapla" 
                                Width="150"
                                VerticalContentAlignment="Center"
                                Background="Transparent" BorderThickness="0" 
                                Margin="15"
                                FontWeight="Bold"
                                Foreground="White"
                                Click="btnHesapla_Click"/>
                    </Border>
               
                    
                </StackPanel>
                
                <StackPanel Orientation="Horizontal" Height="30" VerticalAlignment="Top" Margin="10 200,0,0" HorizontalAlignment="Center">
                    <Border CornerRadius="10,0,0,10" Background="White">
                        <Label Content="Sonuç :" VerticalContentAlignment="Center" Width="150"  HorizontalContentAlignment="Right" FontWeight="Bold"/>
                    </Border>
                    <Border CornerRadius="0,10,10,0" Background="White" >
                        <Label x:Name="lblSonuc" Content="?" VerticalContentAlignment="Center" Width="150"  HorizontalContentAlignment="Left" FontWeight="Bold"/>
                    </Border>


                </StackPanel>

            </Grid>
        </Border>
    </Grid>
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

namespace WpfApp1
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

        private void btnHesapla_Click(object sender, RoutedEventArgs e)
        {
            int sayi1 = Convert.ToInt32(txtSayi1.Text);
            int sayi2 = Convert.ToInt32(txtSayi2.Text);

            double sonuc = 0;

            if (rbTopla.IsChecked==true)
            {
                sonuc = sayi1 + sayi2;
            }else if (rbCikart.IsChecked == true)
            {
                sonuc = sayi1 - sayi2;
            }
            else if (rbCarp.IsChecked == true)
            {
                sonuc = sayi1 * sayi2;
            }
            else if (rbBol.IsChecked == true)
            {
                sonuc = sayi1 / sayi2;
            }
            lblSonuc.Content = sonuc.ToString();
        }
    }
}

```
