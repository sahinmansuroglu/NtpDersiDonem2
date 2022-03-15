## Menu Kontrolü ##

**Ekran Arayüzü**

![image](https://user-images.githubusercontent.com/28144917/158318470-ce8d3136-7737-4259-baa5-8652b79b2dce.png)

![image](https://user-images.githubusercontent.com/28144917/158318762-5709f37b-76e6-4a66-859b-f00733dfe558.png)

![image](https://user-images.githubusercontent.com/28144917/158318816-fc7e7852-1779-4222-a115-6c57caf5f2aa.png)

**Arayüzün XAML kodları**
```xaml
<Window x:Class="WpfApp42.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp42"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <DockPanel>
        <Menu DockPanel.Dock="Top">
            <MenuItem Header="_Düzenle">
                <MenuItem Header="Kopyala" Command="ApplicationCommands.Copy"/>
                <MenuItem   Header="Kes" Command="ApplicationCommands.Cut">
                    <MenuItem.Icon>
                        <Image Source="cut.png" Width="15" Height="15" />
                    </MenuItem.Icon>
                </MenuItem>
                <MenuItem Header="Yapıştır" Command="ApplicationCommands.Paste"/>
            </MenuItem>
            <MenuItem Header="_Yazı fontu">
                <MenuItem Header="Kalı_n" IsCheckable="True"
                          Checked="Kalin_Checked"
                            Unchecked="Kalin_Unchecked"/>
                <MenuItem Header="_Italic" 
                          IsCheckable="True"
                          Checked="Italic_Checked"
                          Unchecked="Italic_Unchecked"/>
                <Separator/>
                <MenuItem Header="Y_azı Büyüklüğü Arttır"
                            Click="FontArttir_Click"/>
                <MenuItem Header="Y_azı Büyüklüğü Azaşt"
              Click="FontAzalt_Click"/>
            </MenuItem>
        </Menu>
        <TextBox Name="textBox1" TextWrapping="Wrap"
         Margin="2" >
            C# Programlama Dili ile Masaüstü uygulamaları geliştirilebilir.
        </TextBox>
    </DockPanel>
</Window>

```
**Arkaplanda çalışan C# kodları**

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

namespace WpfApp42
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
        private void Kalin_Checked(object sender, RoutedEventArgs e)
        {
            textBox1.FontWeight = FontWeights.Bold;
        }

        private void Kalin_Unchecked(object sender, RoutedEventArgs e)
        {
            textBox1.FontWeight = FontWeights.Normal;
        }

        private void Italic_Checked(object sender, RoutedEventArgs e)
        {
            textBox1.FontStyle = FontStyles.Italic;
        }

        private void Italic_Unchecked(object sender, RoutedEventArgs e)
        {
            textBox1.FontStyle = FontStyles.Normal;
        }

        private void FontArttir_Click(object sender, RoutedEventArgs e)
        {
            if (textBox1.FontSize < 18)
            {
                textBox1.FontSize += 2;
            }
        }

        private void FontAzalt_Click(object sender, RoutedEventArgs e)
        {
            if (textBox1.FontSize > 10)
            {
                textBox1.FontSize -= 2;
            }
        }
    }
}

```

[Uygulamanın Tamamlanmış Hali İçin Tıklayınız](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8250650/WpfApp42.zip)
