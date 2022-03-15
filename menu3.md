## ToolBar Kontrolü ##


![image](https://user-images.githubusercontent.com/28144917/158356315-0000b271-c5f7-415d-81bb-769cadccfbe5.png)


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
        <ToolBarTray DockPanel.Dock="Top">
            <ToolBar>
                <Button x:Name="btnSil"  ToolTip="Yazıyı Sil" Click="btnSil_Click" >
                    <Image Width="20"   Source="delete1.png" ></Image>
                </Button>
                <Separator/>
                <Label>Yazı Boyutu</Label>
                <ComboBox Name="cbYaziBoyutu" SelectionChanged="cbYaziBoyutu_SelectionChanged" SelectedValuePath="Content"  >
                    <ComboBoxItem>10</ComboBoxItem>
                    <ComboBoxItem >12</ComboBoxItem>
                    <ComboBoxItem IsSelected="True">14</ComboBoxItem>
                    <ComboBoxItem>16</ComboBoxItem>
                </ComboBox>
            </ToolBar>
        </ToolBarTray>
        <TextBox x:Name="txtEditor"></TextBox>
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

        private void cbYaziBoyutu_SelectionChanged(object sender, SelectionChangedEventArgs e)
        {
          if(cbYaziBoyutu.SelectedValue != null)
            {
                int yaziBoyutu=Int32.Parse( cbYaziBoyutu.SelectedValue.ToString());

                 txtEditor.FontSize = yaziBoyutu;

            }

           
        }

        private void btnSil_Click(object sender, RoutedEventArgs e)
        {
            txtEditor.Text = "";
        }
    }
}

```

Kullanılan Icon

![delete1](https://user-images.githubusercontent.com/28144917/158356198-3362b65b-c5af-4e1e-8a19-f5dd3deafb36.png)
