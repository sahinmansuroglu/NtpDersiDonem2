
### Ornek-1 ###

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
