### 2. Bölüm Quiz Sorusu-3 ###

> Aşağıdaki Ekran Görüntüsünü tasarlayınız. Yeni Oyun butonuna tıklandığında canvas içerisinde yarım saniye aralıklarla yer değiştiren bir buton görüntülensin ve kullanıcı bu butona tıklamaya çalışsın. Eğer butona tıklayabilirse 5 puan kazansın eğer boşluğa tıklarsa 3 puan  kaybetsin. Skor bolümünde kullanıcının kazandığı puanlar gözüksün. Oyunu Sonlandır butonuna tıklandığında oyun bitirilsin.

> [Uygulamanın Tamamlanmış Haline Ulaşmak için Tıklayınız..](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8115994/WpfApp27.zip)


![image](https://user-images.githubusercontent.com/28144917/155117093-4a875750-95c9-489e-b2be-a526ca3e99f4.png)


**Arayüz kodları**

```xaml
<Window x:Class="WpfApp27.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp27"
        mc:Ignorable="d"
        Title="MainWindow" Height="700" Width="600" ResizeMode="NoResize"
        WindowStyle="None" AllowsTransparency="True" Background="Wheat">
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="100"/>
            <RowDefinition/>
        </Grid.RowDefinitions>

        <Border Grid.Row="0" Background="LightSalmon" CornerRadius="30" Margin="5">
            <StackPanel Orientation="Horizontal" Margin="15">
                <Button x:Name="btnYeniOyun" 
                        Content="Yeni Oyun"
                        Background="#FF930093"
                        Foreground="Yellow"
                        Padding="15"
                        FontSize="15"
                        FontWeight="Bold"
                        Margin="5"
                        Click="btnYeniOyun_Click"   />
                <Button x:Name="btnSonlandır"
                        Content="Oyunu sonlandır"
                        Background="#FF5F3C3C"
                        Foreground="Yellow"
                        Padding="15"
                        FontSize="15"
                        FontWeight="Bold"
                        Margin="5"
                        Click="btnSonlandır_Click"/>
                <Label Content="Skor :"
                       FontSize="40"
                       FontWeight="Bold"
                       Padding="0 -5 0 0 "
                       Margin="60 0 0 0"/>
                <Label Name="lblSkor"
                       Content="000"
                       FontSize="40"
                       FontWeight="Bold"
                       Padding="0 0"
                       HorizontalContentAlignment="Center"
                       Margin="15 0 0 0"
                       BorderBrush="Black"
                       BorderThickness="2"
                       Width="100"
                      />
            </StackPanel>
            
        </Border>

        <Border Grid.Row="1" Background="#FFB9FFB9" CornerRadius="30" Margin="5">
            <Canvas Margin="10"  
                    Background="#FFB9FFB9" 
                    Width="570"
                    Height="554"
                    MouseLeftButtonDown="Canvas_MouseLeftButtonDown"    >
                <Button x:Name="btnTikla" 
                        Content="Tıklayınız"
                        Padding="5"
                        Background="DarkBlue"
                        Foreground="Wheat"
                        FontWeight="Bold"
                        BorderThickness="0"
                        Click="btnTikla_Click"
                        Visibility="Hidden"/>

            </Canvas>

        </Border>

    </Grid>
   
</Window>

```

**C# kodları**

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
using System.Windows.Threading;

namespace WpfApp27
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {

        int skor = 0;
        DispatcherTimer zamanlayici = new DispatcherTimer();
        public MainWindow()
        {
            InitializeComponent();
        }
        private void btnYeniOyun_Click(object sender, RoutedEventArgs e)
        {
            btnTikla.Visibility = Visibility.Visible;
            zamanlayici.Interval= TimeSpan.FromSeconds(0.7);
            zamanlayici.Tick += Zamanlayici_Tick;
            zamanlayici.Start();
        }
        private void Zamanlayici_Tick(object sender, EventArgs e)
        {
            Random random = new Random();
            int x = random.Next(1, 500);
            int y = random.Next(1, 500);

            Canvas.SetLeft(btnTikla, x);
            Canvas.SetTop(btnTikla, y);
        }
        private void btnTikla_Click(object sender, RoutedEventArgs e)
        {
            skor += 5;
            lblSkor.Content = skor.ToString();
        }
        private void Canvas_MouseLeftButtonDown(object sender, MouseButtonEventArgs e)
        {
            skor -= 3;
            if (skor<=0)
            {
                skor = 0;
            }
            lblSkor.Content = skor.ToString();
        }
        private void btnSonlandır_Click(object sender, RoutedEventArgs e)
        {
            zamanlayici.Stop();
            btnTikla.Visibility = Visibility.Hidden;
            lblSkor.Content = 0;
        }
    }
}

```
