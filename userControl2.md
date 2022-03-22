
### Ornek ###

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
        <uc:KarakterSinirlandirmaliTextBox Baslik="Ad Soyad" 
              MaxKarakterSayisi="50" 
              Height="70" Margin="10"/>
              
        <uc:KarakterSinirlandirmaliTextBox 
                  Baslik="Doğum Yeri" 
                  MaxKarakterSayisi="20"
                  Height="70" Margin="10"/>
                  
        <uc:KarakterSinirlandirmaliTextBox 
                    Baslik="Son Mezuniyet" 
                    MaxKarakterSayisi="30" 
                    Height="70" Margin="10"/>
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
