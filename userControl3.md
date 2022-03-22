
### Ornek ###

[Uygulamanın Tamamlanmış Haline ulaşmak için tıklayınız](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8323649/WpfApp53.zip)



![image](https://user-images.githubusercontent.com/28144917/159467553-673df5d8-ccee-4e5e-b4a7-fe34cf7cf0a5.png)



**Klasör Yapısı**

![image](https://user-images.githubusercontent.com/28144917/159467568-b71a49d1-7bbe-46f0-8f49-c9d4326109ec.png)




**UserControl dosyası**

```xaml

<UserControl x:Class="WpfApp53.UserControls.LikeDislike"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
             xmlns:local="clr-namespace:WpfApp53.UserControls"
             mc:Ignorable="d" 
             d:DesignHeight="40" d:DesignWidth="200">
    
    <StackPanel Orientation="Horizontal">
        
        <Image x:Name="imgLike" Source="like.png" 
               Width="25" Height="25"
               Margin="0 -6 0 0" 
               MouseLeftButtonDown="imgLike_MouseLeftButtonDown"   />
        
        <Label Content="{Binding LikeSayisi}" 
               VerticalContentAlignment="Center" 
               Margin="5 0 0 0 "/>
        
        <Image x:Name="imgDislike" Source="dislike.png" 
               Width="25" Height="25" 
               Margin="20 10 0 0" 
               MouseLeftButtonDown="imgDislike_MouseLeftButtonDown"   />
        
        <Label Content="{Binding DislikeSayisi}"
               VerticalContentAlignment="Center" 
               Margin="5 0 0 0 "/>

    </StackPanel>
    
</UserControl>


```


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

namespace WpfApp53.UserControls
{
    /// <summary>
    /// Interaction logic for LikeDislike.xaml
    /// </summary>
    public partial class LikeDislike : UserControl, INotifyPropertyChanged
    {
        public LikeDislike()
        {
            InitializeComponent();
            this.DataContext = this;
        }

        private void Image_MouseLeftButtonDown(object sender, MouseButtonEventArgs e)
        {
            MessageBox.Show("Ok");

        }

        private int likeSayisi=0;

        public int LikeSayisi
        {
            get { return likeSayisi; }
            set {
                
                likeSayisi = value;
                OnPropertyChanged("LikeSayisi");
            }
        }
        private int dislikeSayisi=0;

        public int DislikeSayisi
        {
            get { return dislikeSayisi; }
            set { dislikeSayisi = value;
                OnPropertyChanged("DislikeSayisi");
            }
        }

        private void imgLike_MouseLeftButtonDown(object sender, MouseButtonEventArgs e)
        {
            LikeSayisi++;
        }

        private void imgDislike_MouseLeftButtonDown(object sender, MouseButtonEventArgs e)
        {
            DislikeSayisi++;
         //   MessageBox.Show(DislikeSayisi.ToString());

        }

        protected internal virtual void OnPropertyChanged(string propertyName)
        {
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
        }

        public event PropertyChangedEventHandler PropertyChanged;
    }
}

```

**MainWindow dosyası**

```xaml

<Window x:Class="WpfApp53.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp53"
        xmlns:userKont="clr-namespace:WpfApp53.UserControls"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="300">
    <StackPanel>
        <userKont:LikeDislike  Margin="10"/>
        <userKont:LikeDislike  Margin="10"/>
        <userKont:LikeDislike x:Name="likeDislike3"  Margin="10"/>
        <userKont:LikeDislike  Margin="10"/>
        <Button x:Name="button" Content="Tıklayınız" 
                Margin="10" 
                Padding="10"
                Click="button_Click"/>
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

namespace WpfApp53
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

        private void button_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show($"{likeDislike3.LikeSayisi}  {likeDislike3.DislikeSayisi}");
                
                }
    }
}


```
