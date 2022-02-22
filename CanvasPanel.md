## Canvas Panel Kullanımı ##
> Canvas paneli, içerisindeki nesneleri soldan, sağdan, yukarıdan veya aşağıdan  uzaklık vererek   yerleştirmemize olanak sağlayan panel türüdür.


| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/154909555-3823910f-dd5a-4677-8fba-84a635076d45.png)|![image](https://user-images.githubusercontent.com/28144917/154909493-1d8e9eac-3538-49fc-860d-e4297c526cfc.png)|
|![image](https://user-images.githubusercontent.com/28144917/154909925-ac2c6206-b7db-4c53-a2c1-db17221f7317.png)|![image](https://user-images.githubusercontent.com/28144917/154909887-80035876-d25b-42fc-92a1-b1862e2b9974.png)|


### Örnek-1 ###

> Canvas üzerinde  mouse ile tıklanan noktaya kenar uzunlukları 0 - 50 arası random sayı olan  dikdörtgen ekleyen uygulamayı tasarlayınız.

![image](https://user-images.githubusercontent.com/28144917/155094325-02a9bf25-3285-402b-a55e-319b9534b4f3.png)


**Arayüz kodları**

```xaml
<Window x:Class="WpfApp27.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp27"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <Canvas x:Name="Canva" 
            MouseLeftButtonDown="Canva_MouseLeftButtonDown" 
            Background="LightPink">
        
        
    </Canvas>
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

namespace WpfApp27
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

        private void Canva_MouseLeftButtonDown(object sender, MouseButtonEventArgs e)
        {
            
            Point tiklamaKordinat = e.GetPosition(Canva);
           
            Random random = new Random();

            Rectangle dikdortgen = new Rectangle
            {
                Width = random.Next(1,100),
                Height = random.Next(1, 100),
                Fill = Brushes.DarkBlue

            };

            Canva.Children.Add(dikdortgen);
            Canvas.SetLeft(dikdortgen, tiklamaKordinat.X);
            Canvas.SetTop(dikdortgen, tiklamaKordinat.Y);
        }
    }
}

```
### Örnek-2 ###

> Aşağıdaki Ekran Görüntüsünü tasarlayınız. Yeni Oyun butonuna tıklandığında canvas içerisinde yarım saniye aralıklarla yer değiştiren bir buton görüntülensin ve kullanıcı bu butona tıklamaya çalışsın. Eğer butona tıklayabilirse 1 puan kazansın eğer boşluğa tıklarsa 2 puan  kaybetsin. Skor bolümünde kullanıcının kazandığı puanlar gözüksün. Bitir butonuna tıklandığında oyun bitirlsin.



<Window x:Class="WpfApp25.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp25"
        mc:Ignorable="d"
        Title="MainWindow" Height="400" Width="400">
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="40"/>
            <RowDefinition Height="40*"/>

        </Grid.RowDefinitions>
        <Button x:Name="btnBasla" Margin="5" Content="Basla" Click="btnBasla_Click" />
        <Canvas Background="Red"  Grid.Row="1" Grid.Column="0" Margin="10" Name="cnv" MouseLeftButtonDown="cnv_MouseLeftButtonDown" >
            <Button x:Name="btnTikla" Content="Tıklayınız" Click="btnTikla_Click"   />
        </Canvas>
    </Grid>
    
</Window>


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

namespace WpfApp25
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
        System.Windows.Threading.DispatcherTimer dispatcherTimer = new System.Windows.Threading.DispatcherTimer();

        private void cnv_MouseLeftButtonDown(object sender, MouseButtonEventArgs e)
        {
            Point a= e.GetPosition(cnv);
            MessageBox.Show($"{a.X} {a.Y}");
        }

        private void btnBasla_Click(object sender, RoutedEventArgs e)
        {
            dispatcherTimer.Tick += DispatcherTimer_Tick;
            dispatcherTimer.IsEnabled = true;
            dispatcherTimer.Interval = new TimeSpan(0, 0, 1);

        }

        private void DispatcherTimer_Tick(object sender, EventArgs e)
        {
           // MessageBox.Show(cnv.Height.ToString());
            Random rnd = new Random();

            int x = rnd.Next(1,400);
            int y = rnd.Next(1, 400);

            Canvas.SetLeft(btnTikla, x);
            Canvas.SetTop(btnTikla, y);
        }

        private void btnTikla_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("okk");
        }
    }
}

