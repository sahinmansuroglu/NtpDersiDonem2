##  Quiz Sorusu ##


| Ekran Görüntüsü |Arayüzün Basit Anahat Yapısı|Arayüzün Ayrıntılı Anahat Yapısı|
|:--------:|:----------------------------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/153723052-a15cef98-629d-4351-b124-2dcfad03baa4.png)|![image](https://user-images.githubusercontent.com/28144917/153724252-bcd19047-0bbf-4663-b88c-c98392289c0c.png)|![image](https://user-images.githubusercontent.com/28144917/153724232-4a029462-59b8-477b-9d9d-465586219861.png)|

[Uygulamanın Tamamlanmış Hali için tıklayınız](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8054260/WpfApp1.zip)

> **Aşağıda Verilenleri sırasıyla uygulayarak yukarıda görselleri verilen WPF uygulamasını   tasarlayınız.**
 
1. Ana Window'un yüksekliğini 300px, genişliğini de 280px olarak ayarlayınız.
2. Ana Window'un içerisinde "BorderEnDis" adında  olan bir border oluşturun. (özellikleri: CornerRadius="25" Background="#FF8000FF" Padding="20" )
3. "BorderEnDis" adlı border'in içerisinde  "Grid1" adında ve genişliği 250px olan bir grid oluşturun.
4. "Grid1" adlı grid'in içerisinde  "StackPanelDikey" adında bir StackPanel oluşturunuz(özellikleri: Orientation="Vertical"  VerticalAlignment="Top" Margin="10")
5. StackPanelDikey adlı StackPanel İçerisine "Border1","Border2","Border3", "Border4" ve "Border5" adlarında 5 adet Border nesnesi ekleyin.
6. Beşinci adımda oluşturuluna 5 Adet Border nesnesinin Özellikleri:CornerRadius="10,10,10,10" Background="White" Margin="0 10 0 10"
7. "Border1","Border2" ve "Border5" adlı Border nesnesilerinin herbirinin içerisine genişliği 200 olan Grid nesnesi oluşturun.
8. Border1 içerisindeki Grid'in içerisine 
   - Content'i "1. Sayı" olan aşağıdaki özelliklerde bir label nesnesi ekleyin
      -  VerticalContentAlignment="Center" Width="100" FontWeight="Bold" HorizontalAlignment="Left"
   - adı txtSayi1 olan aşağıdaki özelliklerde bir TextBox nesnesi ekleyin
      -  VerticalContentAlignment="Center" Width="100" Margin="2" HorizontalAlignment="Right"
9. Border2 içerisindeki Grid'in içerisine 
   - Content'i "2. Sayı" olan aşağıdaki özelliklerde bir label nesnesi ekleyin
      -  VerticalContentAlignment="Center" Width="100" FontWeight="Bold" HorizontalAlignment="Left"
   - adı txtSayi2 olan aşağıdaki özelliklerde bir TextBox nesnesi ekleyin
      -  VerticalContentAlignment="Center" Width="100" Margin="2" HorizontalAlignment="Right"
10. Border3 içerisine Orientation="Horizontal" özelliğinde bir StackPanel Ekleyiniz.
11. Border3 içerisindeki StackPanel içerisine;
    - "rbTopla" adında Content'i "topla" olan radioButton ekleyiniz.
    - "rbCikart" adında Content'i "Çıkart" olan radioButton ekleyiniz.
    - "rbCarp" adında Content'i "Çarp" olan radioButton ekleyiniz.
    - "rbBol" adında Content'i "Böl" olan radioButton ekleyiniz.
    - Oluşturulan Tüm Radio Butonların Özellikleri: VerticalAlignment="Center" FontWeight="Bold" Margin="5"
12. Border4  içerisindeki aşağıdaki özelliklerde "btnHesapla" adında Content'i "Hesapla" olan bir button nesnesi ekleyiniz. 
    - Width="150"   VerticalContentAlignment="Center"  Background="Transparent" 
    - BorderThickness="0"   Margin="5"   FontWeight="Bold"   Foreground="White"
    - **Not:** Border4'un arka plan rengi black olarak ayarlanacak.
13. Border5 içerisindeki Grid'in içerisine 
    - Content'i "Sonuç" olan aşağıdaki özelliklerde bir label nesnesi ekleyin
      -  VerticalContentAlignment="Center" Width="100" FontWeight="Bold" HorizontalAlignment="Left"
    - Adı "lblSonuc", Content'i "?" olan aşağıdaki özelliklerde bir label nesnesi ekleyin
      -  VerticalContentAlignment="Center" Width="100" Margin="2" HorizontalAlignment="Right"
14. Buton'un tıklanma olayı için bir metod ekleyiniz ve bu metot içerisinde butona tıklandığında girilen sayılara seçilen işlemi yaptırtıp sonucu lblSonuc adlı Label nesnesinde görüntületiniz.
15. Son olarak ana window'a  aşağıdaki özellikleri ekleyiniz.
    -  WindowStyle="None"          AllowsTransparency="True"          Background="Transparent"

### Çözümün XAML kodları ###

```xaml
<Window x:Class="WpfApp1.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp1"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="280" 
        WindowStyle="None"
    AllowsTransparency="True"
        Background="Transparent"
        >
    
        <Border x:Name="BorderEnDis" CornerRadius="25" Background="#FF8000FF" Padding="20">
            <Grid x:Name="Grid1" Width="250" >
                <StackPanel x:Name="StackPanelDikey" Orientation="Vertical"  VerticalAlignment="Top" Margin="10" >
                    <Border x:Name="Border1" CornerRadius="10,10,10,10" Background="White" Margin="0 10 0 10">
                        <Grid Width="200">
                            <Label Content="1. Sayı" VerticalContentAlignment="Center" Width="100" FontWeight="Bold" HorizontalAlignment="Left"/>
                            <TextBox x:Name="txtSayi1" VerticalContentAlignment="Center" Width="100" Margin="2" HorizontalAlignment="Right" />
                        </Grid>
                       
                    </Border>
                    <Border x:Name="Border2" CornerRadius="10,10,10,10" Background="White" Margin="0 0 0 10">
                        <Grid Width="200">
                            <Label Content="2. Sayı" VerticalContentAlignment="Center" Width="100" FontWeight="Bold" HorizontalAlignment="Left"/>
                            <TextBox x:Name="txtSayi2" VerticalContentAlignment="Center" Width="100" Margin="2" HorizontalAlignment="Right" />
                        </Grid>

                    </Border>
                    <Border x:Name="Border3" CornerRadius="10,10,10,10" Background="White" Height="30">
                        <StackPanel Orientation="Horizontal">
                        <RadioButton x:Name="rbTopla" GroupName="islem" Content="Topla" VerticalAlignment="Center" FontWeight="Bold" Margin="5" />
                        <RadioButton x:Name="rbCikart" GroupName="islem" Content="Çıkart" VerticalAlignment="Center" FontWeight="Bold" Margin="5"/>
                        <RadioButton x:Name="rbCarp" GroupName="islem" Content="Çarp" VerticalAlignment="Center" FontWeight="Bold" Margin="5"/>
                        <RadioButton x:Name="rbBol" GroupName="islem" Content="Böl" VerticalAlignment="Center" FontWeight="Bold" Margin="5"/>

                    </StackPanel>

                    </Border>
                    <Border x:Name="Border4" CornerRadius="10,10,10,10" Background="#FF1A1123" Margin="0 10 0 0">
                        <Button x:Name="btnHesapla" Content="Hesapla" 
                                    Width="150"
                                    VerticalContentAlignment="Center"
                                    Background="Transparent" BorderThickness="0" 
                                    Margin="5"
                                    FontWeight="Bold"
                                    Foreground="White"
                                    Click="btnHesapla_Click"/>
                    </Border>
                    <Border CornerRadius="10,10,10,10" Background="White" Margin="0 10 0 10">
                    <Grid Width="200">
                        <Label Content="Sonuç :" Width="100" HorizontalAlignment="Left" FontWeight="Bold"/>
                        <Label x:Name="lblSonuc" Content="?" Width="100"  HorizontalAlignment="Right" FontWeight="Bold"/>

                    </Grid>

                </Border>
            </StackPanel>

               

                

             

            </Grid>
        </Border>

</Window>


```



### Çözümün C# kodları ###

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

namespace WpfApp1
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

        private void btnHesapla_Click(object sender, RoutedEventArgs e)
        {
            int sayi1 = Convert.ToInt32(txtSayi1.Text);
            int sayi2 = Convert.ToInt32(txtSayi2.Text);

            double sonuc = 0;

            if (rbTopla.IsChecked==true)
            {
                sonuc = sayi1 + sayi2;
            }else if (rbCikart.IsChecked == true)
            {
                sonuc = sayi1 - sayi2;
            }
            else if (rbCarp.IsChecked == true)
            {
                sonuc = sayi1 * sayi2;
            }
            else if (rbBol.IsChecked == true)
            {
                sonuc = sayi1 / sayi2;
            }
            lblSonuc.Content = sonuc.ToString();
        }
    }
}

```
