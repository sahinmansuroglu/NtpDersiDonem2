## ContextMenu Kontrolü ##


![image](https://user-images.githubusercontent.com/28144917/158360818-71627694-302a-44d5-bbf7-1c4700768e8e.png)


```xaml

<Window x:Class="WpfApp42.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp42"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="300">
    <DockPanel>
       
        <TextBox Name="textBox1" TextWrapping="Wrap"
         Margin="2" >
            <TextBox.ContextMenu>
                <ContextMenu>
                    <MenuItem Header="Kalın" IsCheckable="True"
                          Checked="Kalin_Checked"
                            Unchecked="Kalin_Unchecked"/>
                    <MenuItem Header="Italic" 
                          IsCheckable="True"
                          Checked="Italic_Checked"
                          Unchecked="Italic_Unchecked"/>
                    <Separator/>
                    <MenuItem Header="Yazı Büyüklüğü Arttır"
                            Click="FontArttir_Click"/>
                    <MenuItem Header="Yazı Büyüklüğü Azalt"
              Click="FontAzalt_Click"/>

                </ContextMenu>
                
            </TextBox.ContextMenu>
            
            C# Programlama Dili ile Masaüstü uygulamaları geliştirilebilir.
        </TextBox>
    </DockPanel>
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
