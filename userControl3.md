
### Ornek ###

![image](https://user-images.githubusercontent.com/28144917/159444268-fa48fa50-f73a-40d5-bc87-42d04c3d497f.png)


**Klasör Yapısı**

![image](https://user-images.githubusercontent.com/28144917/159444287-67f9bfa6-9a7b-4cfe-ba33-50c01c3ec92f.png)



**UserControl C# dosyası**

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

namespace WpfApp50.UserControls
{
    /// <summary>
    /// Interaction logic for LikeDislikeKontrol.xaml
    /// </summary>
    public partial class LikeDislikeKontrol : UserControl, INotifyPropertyChanged
    {
        public LikeDislikeKontrol()
        {
            InitializeComponent();
            this.DataContext = this;
        }

    

        private int likeCount;

        public int LikeCount
        {
            get { return likeCount; }
            set
            {
                likeCount = value;
                OnPropertyChanged("LikeCount");
            }
        }

        private int dislikeCount;

        public int DislikeCount
        {
            get { return dislikeCount; }
            set { dislikeCount = value;
                OnPropertyChanged("DislikeCount");
            }
        }



        private void btnLike_Click(object sender, RoutedEventArgs e)
        {
            LikeCount++;
        }

        private void btnDislike_Click(object sender, RoutedEventArgs e)
        {
            DislikeCount++;
            
        }
        protected internal virtual void OnPropertyChanged(string propertyName)
        {
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
        }

        public event PropertyChangedEventHandler PropertyChanged;
    }
}

```


**UserControl dosyası**

```xaml
<UserControl x:Class="WpfApp50.UserControls.LikeDislikeKontrol"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
             xmlns:local="clr-namespace:WpfApp50.UserControls"
             mc:Ignorable="d" 
             d:DesignHeight="50" d:DesignWidth="150"
             Height="50" Width="250">

    <UserControl.Resources>
        <Style TargetType="Label">

            <Setter Property="FontSize" Value="14"/>

            <Setter Property="FontWeight" Value="Bold"/>

        </Style>
        
    </UserControl.Resources>
    <Border BorderBrush="LightGray" BorderThickness="1" Margin="5">
        
   
    <StackPanel Orientation="Horizontal">
        <Button x:Name="btnLike" Background="Transparent" BorderThickness="0" Click="btnLike_Click" >
            <Image Height="30" Width="30" Source="like.png" Margin="0 -8 0 0" ></Image>
        </Button>

        <Label Content="{Binding LikeCount, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}" VerticalContentAlignment="Center"/>
        <Button Margin="20 0 0 0" x:Name="btnDislike" Background="Transparent" BorderThickness="0" Click="btnDislike_Click" >
            <Image Height="30" Width="30" Source="dislike.png" Margin="0 10 0 0" ></Image>
        </Button>

        <Label Content="{Binding DislikeCount}" VerticalContentAlignment="Center"/>
    </StackPanel>
    </Border>
</UserControl>

```

**MainWindow dosyası**

```xaml
<Window x:Class="WpfApp50.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp50"
        xmlns:kulKont="clr-namespace:WpfApp50.UserControls"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="300">
    <StackPanel>

        <kulKont:LikeDislikeKontrol x:Name="kont1" />
        <kulKont:LikeDislikeKontrol />
        <kulKont:LikeDislikeKontrol />
        <kulKont:LikeDislikeKontrol />
        <kulKont:LikeDislikeKontrol />
        <DatePicker />

        <Button Content="Tıklayınız" Click="Button_Click_1" ></Button>
    </StackPanel>
</Window>

```

**MainWindow C# dosyası**

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

namespace WpfApp50
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

   
        private void Button_Click_1(object sender, RoutedEventArgs e)
        {
            MessageBox.Show(kont1.DislikeCount.ToString());
        }
    }
}

```
