### 2. Bölüm Quiz Sorusu-2 ###

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
