## userControl ##

user controller birden fazla UI nesnesinin bir isim altında tanımlanarak  tekrar tekrar kullanılmasına olanak sağlar

### Ornek-1 ###

![image](https://user-images.githubusercontent.com/28144917/159414425-22ed842f-8ca1-4346-8af6-54f2dfe9d1b8.png)


**Klasör Yapısı**
![image](https://user-images.githubusercontent.com/28144917/159414654-7e748c99-b394-49b7-80c1-5dfbc2e55213.png)




**UserControl dosyası**

```xaml
<UserControl x:Class="WpfApp50.UserControls.LabelTexBox"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
             xmlns:local="clr-namespace:WpfApp50.UserControls"
             mc:Ignorable="d" 
             d:DesignHeight="30" d:DesignWidth="200"
             Height="40"
             >
    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition/>
            <ColumnDefinition/>
        </Grid.ColumnDefinitions>

        <Label Name="lblEtiket" Margin="5" Content="Ad Soyad" VerticalAlignment="Center" BorderBrush="#FF382380" BorderThickness="0,0,0,2"/>
        <TextBox Grid.Column="1" x:Name="txtAd" BorderBrush="#FF38446A" Margin="5"/>


    </Grid>
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
        <kulKont:LabelTexBox />
        <kulKont:LabelTexBox />
        <kulKont:LabelTexBox />
        <kulKont:LabelTexBox />
        <kulKont:LabelTexBox />
        <kulKont:LabelTexBox />

    </StackPanel>
</Window>

```




![image](https://user-images.githubusercontent.com/28144917/159241066-38cfbd0a-4c1c-41e5-bdb4-b9f1fbd77ba0.png)


```xaml
<UserControl x:Class="WpfApp10.UserControls.KarakterSinirlandirmaliTextBox"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
             xmlns:local="clr-namespace:WpfApp10.UserControls"
             mc:Ignorable="d" 
             d:DesignHeight="350" d:DesignWidth="350">
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="*" />
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <Label Content="{Binding Baslik}" />
        <Label Grid.Column="1">
            <StackPanel Orientation="Horizontal">
                <TextBlock Text="{Binding ElementName=textBox1, Path=Text.Length}" />
                <TextBlock Text="/" />
                <TextBlock Text="{Binding MaxKarakterSayisi}" />
            </StackPanel>
        </Label>
        <TextBox MaxLength="{Binding MaxKarakterSayisi}" 
                 Grid.Row="1" Grid.ColumnSpan="2" 
                 Name="textBox1" 
                 TextWrapping="Wrap"
                 ScrollViewer.VerticalScrollBarVisibility="Auto"/>
    </Grid>
</UserControl>

```

### Ornek-2 ###
Yukarıdaki Örnekte label Content'leri "Ad Soyad" olarak kalmıştır. Mainwindow'da Label'lara erişim için aşağıdaki örneği inceleyebilirsiniz.
![image](https://user-images.githubusercontent.com/28144917/159418667-992d8f2e-c8cc-4832-a7bd-7e6656abdbce.png)




**UserControl dosyası**

```xaml
<UserControl x:Class="WpfApp50.UserControls.LabelTexBox"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
             xmlns:local="clr-namespace:WpfApp50.UserControls"
             mc:Ignorable="d" 
             d:DesignHeight="30" d:DesignWidth="200"
             Height="40"
             >
    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition/>
            <ColumnDefinition/>
        </Grid.ColumnDefinitions>

        <Label Content="{Binding Baslik}" Margin="5"  VerticalAlignment="Center" BorderBrush="#FF382380" BorderThickness="0,0,0,2"/>
        <TextBox Grid.Column="1" x:Name="txtAd" Text="{Binding Veri}" BorderBrush="#FF38446A" Margin="5"/>
        


    </Grid>
</UserControl>

```
**UserControl C# dosyası**

```csharp
using System;
using System.Collections.Generic;
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
    /// Interaction logic for LabelTexBox.xaml
    /// </summary>
    public partial class LabelTexBox : UserControl
    {
        public LabelTexBox()
        {
            InitializeComponent();
            this.DataContext = this;
           
        }
        public string Baslik { get; set; }
        public string Veri { get; set; }
    }
}

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
        <kulKont:LabelTexBox x:Name="kutuAd" Baslik="Ad Soyad" Veri="Şahin" />
        <kulKont:LabelTexBox  x:Name="kutuYas" Baslik="Yaş"  Veri="40" />
        <kulKont:LabelTexBox Baslik="Doğum Yeri" />
        <kulKont:LabelTexBox Baslik="Doğum Tarihi" />
        <kulKont:LabelTexBox Baslik="Mezuniyet" />
        <kulKont:LabelTexBox Baslik="Kan Grubu" />
        <Button Content="Tıklayınız" Click="Button_Click"/>

    </StackPanel>
</Window>

```

**MainWindow C# dosyası**

```csharp
public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
           
        }

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show(kutuAd.Veri);
        }
    }
```


### Ornek-3 ###

```csharp
 public partial class KarakterSinirlandirmaliTextBox : UserControl
    {
        public KarakterSinirlandirmaliTextBox()
        {
            InitializeComponent();
            this.DataContext = this;
        }
      

        public string Baslik { get; set; }

        public int MaxKarakterSayisi { get; set; }
    }
```

```xaml
<Window x:Class="WpfApp10.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp10"
        xmlns:uc="clr-namespace:WpfApp10.UserControls"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="350">
    <StackPanel>
        <uc:KarakterSinirlandirmaliTextBox Baslik="Ad Soyad" MaxKarakterSayisi="50" Height="70" Margin="10"/>
        <uc:KarakterSinirlandirmaliTextBox Baslik="Doğum Yeri" MaxKarakterSayisi="20" Height="70" Margin="10"/>
        <uc:KarakterSinirlandirmaliTextBox Baslik="Son Mezuniyet" MaxKarakterSayisi="30" Height="70" Margin="10"/>
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

namespace WpfApp10
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
    }
}

```

[WpfApp11.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8315727/WpfApp11.zip)

