## StatusBar Kontrolü ##

![image](https://user-images.githubusercontent.com/28144917/158365822-31b1022b-74bc-4def-b303-86d4e3ef5988.png)


```xaml
<Window x:Class="WpfApp44.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp44"
        mc:Ignorable="d"
        Title="Metin Editörü" Height="450" Width="400">
    <DockPanel >
       
       
        <StatusBar Name="sbar"  DockPanel.Dock="Bottom"
            Background="WhiteSmoke" >

            <StatusBarItem>
                <TextBlock  Name="tbCursorPozisyon">Satir:</TextBlock>
            </StatusBarItem>
            <StatusBarItem>
               
            </StatusBarItem>
            <Separator/>
            <StatusBarItem>
                <TextBlock> Yeni Belge</TextBlock>
            </StatusBarItem>
            <StatusBarItem HorizontalAlignment="Right">
                <Button BorderThickness="0" Background="Transparent" Click="Button_Click">
                    <Image Source="help.png" Width="16" Height="16"/>
                </Button>
                
            </StatusBarItem>
        </StatusBar>
        <TextBox x:Name="txtEditor" SelectionChanged="txtEditor_SelectionChanged"   ></TextBox>
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

namespace WpfApp44
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

       

        private void txtEditor_SelectionChanged(object sender, RoutedEventArgs e)
        {
            int row = txtEditor.GetLineIndexFromCharacterIndex(txtEditor.CaretIndex);
            int col = txtEditor.CaretIndex - txtEditor.GetCharacterIndexFromLineIndex(row);
            tbCursorPozisyon.Text = "Satır " + (row + 1) + ", Karakter " + (col + 1);
        }

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Text Editor Version 1");
        }
    }
}

```
