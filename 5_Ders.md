## Temel WPF nesneleri ##
> WPf Uygulamarında kullanılan bir çok kullanıcı arayüz nesnesi bulunmaktadır. Ancak bölümde sık kullanılan temel nesneler anlatılacaktır. Sonraki bölümlerde yeri geldikçe yeni nesneler de anlatılacaktır.
### 1. Label  ### 
> Ekranda metin Görüntülüyebilmek kullanılan UI nesnesidir. (Tek Satırlık veri için kullanılabilir)

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/152944859-9424b0be-984f-4c4b-946f-4c1d0de1442b.png)|![image](https://user-images.githubusercontent.com/28144917/152944893-1905bf52-531d-4386-a0bd-b3ee43cf0c29.png)| 
|![image](https://user-images.githubusercontent.com/28144917/152947779-58081717-514a-4dbc-8192-e93c848e9b78.png)|![image](https://user-images.githubusercontent.com/28144917/152947829-cbfb5fdb-773e-4ec7-817e-bece7787cc18.png)|

### 2. Textblock  ### 
> Ekranda metin Görüntülüyebilmek kullanılan UI nesnesidir. (Bir ve birden fazla satırdan oluşan veriler için kullanılabilir)

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/153364535-2ffbf114-af75-42c7-aa5e-ba0183b5824c.png)|![image](https://user-images.githubusercontent.com/28144917/153364575-7c2cc814-7527-4a55-b8d5-f1af48e4f671.png)|
|![image](https://user-images.githubusercontent.com/28144917/153364737-22691e18-25f1-4f95-bc69-a88a862c2be3.png)|![image](https://user-images.githubusercontent.com/28144917/153364764-e776e69e-41eb-4a20-9475-1aa9ca482ce6.png)|

### 2. TextBox  ### 
> TextBox kullanıcıdan veri almak için kullanılan UI nesnesidir.

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/152948804-3488911c-c424-42fc-abdf-9b87f8829585.png)|![image](https://user-images.githubusercontent.com/28144917/152948796-96145dea-337d-4301-a3de-de5807115858.png)|
|||

#### TextBox Örneği ####
>Wpf penceresinin ortasında bir Label ve Textbox (name:txtMetin) ekleyiniz.Label İçerisinde "Metin Giriniz". Eğer text kutusuna girilen metin Galatasaray ise ekrana "Şampiyon" Mesajı yazdırınız. 
>**Not:** Bu işlem için textBox'in KeyUp olayından yararlanınız

**Ekran Çıktısı**

![image](https://user-images.githubusercontent.com/28144917/152950428-42849486-94ee-4e22-8223-fa8a3fcf39ba.png)

**XAML kodları**
```xaml
<Window x:Class="WpfApp15.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp15"
        mc:Ignorable="d"
        Title="MainWindow" Height="200" Width="200">
    <Grid>
       
        <Label
            Content="Bir Metin Giriniz"
            VerticalAlignment="Top"
            HorizontalAlignment="Center"
            FontSize="15"/>
        
        <TextBox
            x:Name="txtMetin"
         
            FontSize="15"
            FontWeight="Bold"
            Width="150"
            Height="60"
            BorderBrush="Red"
            BorderThickness="2"
            VerticalContentAlignment="Center" 
            KeyUp="txtMetin_KeyDown"  
            />
    </Grid>
</Window>

```

**C# kodları**
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

namespace WpfApp15
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

        private void txtMetin_KeyUp(object sender, KeyEventArgs e)
        {
            if (txtMetin.Text=="Galatasaray")
            {
                MessageBox.Show("Şampiyon....");
            }
            

        }
    }
}

```

### 3. Button  ### 
> Butonlar üzerinde gelinip tıklanıldığında istebilen görevlerin yerine getirilebilmesini sağlayan UI nesnesidir.

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/152952727-bdc6f3d4-aad4-4011-a80c-04f725134f1c.png)|![image](https://user-images.githubusercontent.com/28144917/152952669-f1aa21d6-d7d9-4678-ad92-f4b16cafda75.png)|
|![image](https://user-images.githubusercontent.com/28144917/152952338-00d488d2-a03c-4e1b-b631-ac5eb34108ee.png)|![image](https://user-images.githubusercontent.com/28144917/152952284-9ce6fb49-562b-42c7-8d63-ed274ae01399.png)|

#### Button Örneği-1 ####
> Wpf Penceresinin ortasına genişliği 75 yuksekliği 40 olan bir button ekleyiniz. Butona her tıklandığında tıklandığında 0 ile 100 arası bir sayıyı butonun üzerinde gösterin.

**XAML kodları**
```xaml
<Window x:Class="WpfApp15.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp15"
        mc:Ignorable="d"
        Title="MainWindow" Height="200" Width="200">
    <Grid>

        <Button
            x:Name="buton2"
            Content="Tıklayınız.."
            FontSize="15"
            FontWeight="Bold"
            Width="150"
            Height="60"
            Background="BlanchedAlmond"
            BorderBrush="Red"
            BorderThickness="2"
            Click="buton2_Click"
               
        />
        
    </Grid>
</Window>

```

**C# kodları**
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

namespace WpfApp15
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

        private void buton2_Click(object sender, RoutedEventArgs e)
        {
            Random random = new Random();
            int rastgeleSayi = random.Next(1, 100);
            buton2.Content = $"Tıklayınız : {rastgeleSayi}";


        }
    }
}

```
#### Button Örneği-2 ####
> Wpf Penceresinin ortasına genişliği 75px, yuksekliği 40px,  content'i "Tıklayınız" olan bir button ekleyiniz. Butona tıklanıldığında pencerenin sol üst köşesine Content'i "Buton1", sağ üst köşesine de Content'i "Buton2" olan bir buton ekletiniz. Buton1'e tıklandığında "Buton1 e tıkladınız"  Buton2'e tıklandığında ise "Buton2 ye tıkladınız" şekli ne mesaj görüntülesin
**XAML kodları**

```xaml
<Window x:Class="WpfApp18.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp18"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="300">
    <Grid x:Name="grid1" >
        <Button 
            x:Name="btnTikla"
            Content="Tıklayınız "
            Width="75"
            Height="40"
            Click="btnTikla_Click"  
 
            />
    </Grid>
</Window>

```
**C# kodları**
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

namespace WpfApp18
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

        private void btnTikla_Click(object sender, RoutedEventArgs e)
        {
            Button btn1 = new Button
            {
                Content = "Buton1",
                Width = 100,
                Height = 40,
                VerticalAlignment=VerticalAlignment.Top,
                HorizontalAlignment=HorizontalAlignment.Left

            };

            Button btn2 = new Button
            {
                Content = "Buton2",
                Width = 100,
                Height = 40,
                VerticalAlignment = VerticalAlignment.Top,
                HorizontalAlignment = HorizontalAlignment.Right

            };

            btn1.Click += Btn1_Click;
            btn2.Click += Btn2_Click;

            grid1.Margin = new Thickness(10);

            grid1.Children.Add(btn1);
            grid1.Children.Add(btn2);
        }

        private void Btn2_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Buton2'ye tıklandı");
        }

        private void Btn1_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Buton1'e tıklandı");
        }
    }
}

```
### 4. CheckBox  ### 
> Onay kutusu, kullanıcının ikili bir seçim yapmasına, yani iki olası durumdan sadece birin seçebilmesini sağlayan UI nesnesidir.

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/152971840-a24351b2-34e4-41ae-84ae-7969ba41dbe5.png)|![image](https://user-images.githubusercontent.com/28144917/152971877-bdeef89a-7de2-47c0-b60a-41ce73bf5c14.png)|
|![image](https://user-images.githubusercontent.com/28144917/152972215-aac291c7-01e6-4bb2-b50a-b2afd9fd7bc0.png)|![image](https://user-images.githubusercontent.com/28144917/152972220-877bd43d-87ee-45cf-9851-a856a04922eb.png)|
|![image](https://user-images.githubusercontent.com/28144917/152972893-79697098-0e66-47d9-9106-7333bdfbf6dc.png)| ![image](https://user-images.githubusercontent.com/28144917/152972920-150f53e7-4b2e-4b0f-94ea-83f5fa8fb990.png)|
#### CheckBox Örneği ####
> Aşağıdaki Ekran Tasarımı yapınız. Eğer Checkbox kutusu onaylanırsa butonu aktifleştirilsin. Eğer onay kaldırılırsa buton pasif hale getirilsin.
> Ek olarak butona  tıklandığında "Bilgieriniz kaydedilmiştir" şeklinde mesaj görüntülensin.

![image](https://user-images.githubusercontent.com/28144917/152978925-4841a469-e59a-4a2f-b73b-46aa7e8cabb1.png)

**XAML kodları**

```xaml
<Window x:Class="WpfApp15.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp15"
        mc:Ignorable="d"
        Title="MainWindow" Height="150" Width="300">
    <Grid>

        <CheckBox 
            x:Name="chbOnay"
            Content="Bilgilerimin Doğruluğunu Onaylıyorum"
            VerticalAlignment="Center"
            Foreground="Red"
            FontSize="14"
            BorderBrush="Red"
            BorderThickness="3"
            Padding="5 0 0 0"
            HorizontalAlignment="Left"
            Margin="15,0,0,0"
            Click="chbOnay_Click"  
         />

        <Button
            Name="btnOnay"
            Width="90"
            Height="30"
            Content="Bilgileri Kaydet"
            HorizontalAlignment="Right"
            VerticalAlignment="Bottom"
            Margin="0,0,5,5"
            IsEnabled="False"
            />
    </Grid>
</Window>

```

**C# kodları**
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

namespace WpfApp15
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

        

        private void chbOnay_Click(object sender, RoutedEventArgs e)
        {
            if (chbOnay.IsChecked==true)
            {
                //MessageBox.Show("butonu Aktifle");
                btnOnay.IsEnabled = true;

            }
            else
            {
                btnOnay.IsEnabled = false;
                //MessageBox.Show("butonu Pasifle");
            }
        }

        private void btnOnay_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Bilgieriniz kaydedilmiştir");
        }
    }
}

```
### 5. RadioButton  ### 
> İki yada daha çok seçenek içerisinden tek bir seçin yapabilmek için kullanılan UI nesnesidir.
##### Not: Verilen Örneklerde StackPanel ve Border kullanılmıştır bilgi almak için linklere tıklayabilirsiniz. #####

1. [Border Kullanımı ile ilgili bilgi almak için buraya tıklayınız](https://github.com/sahinmansuroglu/NtpDersiDonem2/blob/main/borderKullanimi.md)
2. [StackPanel Kullanımı ile ilgili bilgi almak için buraya tıklayınız](https://github.com/sahinmansuroglu/NtpDersiDonem2/blob/main/StackPanel.md)

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/153394884-27edcba3-b333-4a54-b222-d6dc04b7d359.png)|![image](https://user-images.githubusercontent.com/28144917/153394921-971e5938-4de5-49e5-be2e-0c6a01e3ebbd.png)|
|![image](https://user-images.githubusercontent.com/28144917/153394551-fad381d3-89db-4c91-9d34-8b2f7d14c72a.png)|![image](https://user-images.githubusercontent.com/28144917/153394599-4ad3aa27-38e1-4925-b456-b22cf38cc94f.png)|

#### RadioButton Örneği ####
> Aşağıdaki Ekran görüntüsünü tasarlayınız. Ardından onayla butonuna tıklandığında girilen metini seçilen renkte olacak şekilde kırmızı çerçeveli label içerisinde görüntüleyen c# kodunu yazınız.

![image](https://user-images.githubusercontent.com/28144917/153409890-872931e8-b985-4508-a9e4-00540fa30519.png)


**XAML kodları**

```xaml
<Window x:Class="WpfApp18.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp18"
        mc:Ignorable="d"
        Title="MainWindow" Height="240" Width="200">
    <Border 
        Background="LightBlue"
        Margin="5"
        CornerRadius="5"
        Padding="10">
    <StackPanel Orientation="Vertical">
            <Label Content="Renk Seçiniz."
                   HorizontalContentAlignment="Center"
                   BorderThickness="0 0 0 2"
                   BorderBrush="DarkBlue"
                   /> 

            <StackPanel Orientation="Horizontal" Margin="10" >
                <RadioButton x:Name="rbKirmizi"  Content="Kırmızı"/>
                <RadioButton  x:Name="rbMavi" Content="Mavi" Margin="15 0 0 0"/>
            </StackPanel>
        <Label Content="Metin Giriniz"
                HorizontalContentAlignment="Center"
                   BorderThickness="0 0 0 2"
                   BorderBrush="DarkBlue"/>
        <TextBox x:Name="txtMetin" Margin="10" Height="25" />
        <Button 
            x:Name="btnOnayla" 
            Content="Onayla" 
            Click="btnOnayla_Click"/>

        <Label x:Name="lblBilgi"
               Height="30" 
               BorderThickness="1"
               BorderBrush="LightCoral"
               Margin="5"
               HorizontalContentAlignment="Center"
               VerticalContentAlignment="Center"/>







    </StackPanel>

    </Border>


</Window>

```


**C# kodları**
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

namespace WpfApp18
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

        

        private void btnOnayla_Click(object sender, RoutedEventArgs e)
        {
            if (rbKirmizi.IsChecked==true)
            {
                lblBilgi.Foreground = Brushes.Red;
            }
            if (rbMavi.IsChecked == true)
            {
                lblBilgi.Foreground = Brushes.Blue;
            }
            lblBilgi.Content = txtMetin.Text;
        }
    }
}

```
### 6. ComboBox  ### 
> Aşağıya doğru açılır liste oluşturmak için kullanılan UI nesnesidir

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/153814785-d1562755-ee30-4081-964b-23188f6f9fc2.png)|![image](https://user-images.githubusercontent.com/28144917/153814884-dd149473-d0b7-44df-8985-4f01c05185df.png)|
|![image](https://user-images.githubusercontent.com/28144917/153815025-1b8af4f5-192d-4252-ba4f-8ec105a29a3e.png)|![image](https://user-images.githubusercontent.com/28144917/153814980-07704f65-75ca-443a-9d76-f4270670083a.png)|


####  ComboBox Örnek ####
> Aşağıdaki Örnekte Şu işlemler yapılmaktadir;

        - Herhangi bir şehir seçildiği zaman kırmızı kenarlıklı label içerisinde seçili şehir gösterilmektedir
        - Şehir Sil butonuna tıklandığında seçili şehir combobox'dan sildirilmiştir.
        - text kutusuna şehir adı girilip Şehir ekle butonuna tıklandığında girilen şehir combobox'a ekletilmiştir.


![image](https://user-images.githubusercontent.com/28144917/153820903-46199105-492c-4f77-91b0-bcb4e0a0febb.png)


**XAML kodları**

```xaml
<Window x:Class="WpfApp19.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp19"
        mc:Ignorable="d"
        Title="MainWindow" Height="420" Width="350">
    <Grid>

        <Border Background="LightBlue" 
                Margin="10"
                CornerRadius="15">
            <StackPanel Margin="10" >
                <Label   Content="Şehir Seçiniz"
                         FontSize="20"
                         HorizontalContentAlignment="Center"
                         BorderThickness="0 0 0 5"
                         BorderBrush="DarkBlue"
                         Margin="0 0 0 15"/>

                <ComboBox Name="cbSehir"  
                          Width="140" 
                          SelectedValuePath="Content"
                          SelectionChanged="cbSehir_SelectionChanged"  >
                    <ComboBoxItem  Content="Adana"/>
                    <ComboBoxItem Content="Mersin"/>
                    <ComboBoxItem Content="İzmir"/>
                    <ComboBoxItem Content="Ankara"/>
                </ComboBox>
              
                <Label Content="Sehir Giriniz"
                       FontSize="20"
                         HorizontalContentAlignment="Center"
                         BorderThickness="0 0 0 5"
                         BorderBrush="DarkBlue"
                         Margin="0 0 0 0"/>
                <TextBox x:Name="txtSehir" Margin="15" FontSize="15" Height="35" HorizontalContentAlignment="Center" VerticalContentAlignment="Center"/>
                <Button x:Name="btnSehirEkle" 
                        Content="Şehir Ekle" 
                        Margin="10" 
                        FontSize="15" 
                        Padding="0 5 0 5"
                        Click="btnSehirEkle_Click"  
                      
                       />
                <Button x:Name="btnSehirSil" 
                        Content="Şehir Sil" 
                        Margin="10" 
                        FontSize="15" 
                        Padding="0 5 0 5"
                        Click="btnSehirSil_Click"
                       />
                <Label Name="lblSeciliSehir" FontSize="10"
                       BorderBrush="Red"
                       BorderThickness="2"
                       Height="40"
                       Margin="15"
                       HorizontalContentAlignment="Center" VerticalContentAlignment="Center"/>

            </StackPanel>
            
            
        </Border>
        
    </Grid>
</Window>

```


**C# kodları**
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

namespace WpfApp19
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

        private void cbSehir_SelectionChanged(object sender, SelectionChangedEventArgs e)
        {

            lblSeciliSehir.Content = cbSehir.SelectedValue.ToString();
          
            
        }

        private void btnSehirEkle_Click(object sender, RoutedEventArgs e)
        {
            cbSehir.Items.Add(txtSehir.Text);
        }

        private void btnSehirSil_Click(object sender, RoutedEventArgs e)
        {
            if (cbSehir.SelectedIndex==-1)
            {
                MessageBox.Show("Lütfen Silinecek Şehir Seçiniz");
            }
            else
            {
                cbSehir.Items.RemoveAt(cbSehir.SelectedIndex);
                lblSeciliSehir.Content = "";
            }
           

        }
    }
}

```
### 7. ListBox  ### 
> Verileri liste halinde görüntülemek için kullanılan UI nesnesidir.

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/154004443-c85be1d0-7405-4a8a-8fbe-48cf96b520ed.png)|![image](https://user-images.githubusercontent.com/28144917/154004516-0c634ba2-4064-4c26-9828-025720d8609b.png)|
|![image](https://user-images.githubusercontent.com/28144917/154004296-8952efaa-3dc2-4e5e-9cea-e4815b8250e1.png)|![image](https://user-images.githubusercontent.com/28144917/154004280-e9f54f0c-5843-4327-b60f-17e705edf2a5.png)|


#### ListBox Örneği  #### 
> Aşağıdaki Örnekte Çalışma Anında ListBox'a veri ekleme ve ver silme işlemi yapılmıştır.

![image](https://user-images.githubusercontent.com/28144917/154015319-6705a25b-e47f-423c-9e77-ff14e9c3889e.png)


**XAML kodları**

```xaml
<Window x:Class="WpfApp20.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp20"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="300">
    <Grid>
        <StackPanel>
            <Label Content="Şehir Adı Giriniz" HorizontalContentAlignment="Center"/>
            <TextBox x:Name="txtSehir" Margin="15 5 15 5" Height="30"/>
            <Button x:Name="btnSehirEkle" 
                    Content="Şehir Ekle" 
                    Margin="15 5 15 5" 
                    Padding="0 5 0 5"
                    Click="btnSehirEkle_Click"  />
            <Button x:Name="btnSehirSil" 
                    Content="Şehir Sil" 
                    Margin="15 5 15 5" 
                    Padding="0 5 0 5"
                    Click="btnSehirSil_Click"/>
            <ListBox x:Name="lbSehirler" Margin="10" Height="100">
                <ListBoxItem Content="Mersin"></ListBoxItem>
                <ListBoxItem Content="Adana"></ListBoxItem>
                <ListBoxItem Content="Ankara"></ListBoxItem>
                <ListBoxItem Content="Van"></ListBoxItem>
            </ListBox>
        </StackPanel>
        
      
    </Grid>
</Window>

```


**C# kodları**
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

namespace WpfApp20
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

        private void btnSehirEkle_Click(object sender, RoutedEventArgs e)
        {
            if (txtSehir.Text.Trim().Length==0)
            {
                MessageBox.Show("Şehir Adı Giriniz...");
            }
            else
            {
                lbSehirler.Items.Add(txtSehir.Text);
                txtSehir.Clear();
            }
            
        }

        private void btnSehirSil_Click(object sender, RoutedEventArgs e)
        {

            if (lbSehirler.SelectedIndex==-1)
            {
                MessageBox.Show("Lütfen ListBox'dan Bir Şehir Seçiniz...");
            }
            else
            {
                int indexNo = lbSehirler.SelectedIndex;

                lbSehirler.Items.RemoveAt(indexNo);
            }
           
           
        }
    }
}

```
### 8. Image  ### 
> Resim görüntülemek için kullanılan UI nesnesidir.

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/154017392-b5ff0bf8-94f9-49f4-bdf7-71d8ba19b372.png)|![image](https://user-images.githubusercontent.com/28144917/154017463-6634311f-fe1e-4a78-9f39-698f9dc1d934.png)|
|![image](https://user-images.githubusercontent.com/28144917/154017656-e7eb7737-3027-45da-9483-5e9d25bfe877.png)|![image](https://user-images.githubusercontent.com/28144917/154017613-752c6f9b-f56d-439b-b162-b1421d6a5001.png)|
|![image](https://user-images.githubusercontent.com/28144917/154017920-3cccc69e-ffa8-4c96-86dd-10c3249a3649.png)|![image](https://user-images.githubusercontent.com/28144917/154017955-7f91e501-aa75-41ac-927b-af0fa08282a3.png)|

####  Image Nesnesi Örneği  ####
> Aşağıdaki Örnekte çalışma anında arayüzdeki butonlara tıklanarak uygun resim ekranda gösterilmiştir.

![image](https://user-images.githubusercontent.com/28144917/154022955-7a90c412-9aaa-4c4c-8b89-d1524c7ac34c.png)


**XAML kodları**

```xaml
<Window x:Class="WpfApp1.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp1"
        mc:Ignorable="d"
        Title="MainWindow" Height="350" Width="300">
    <Grid>
        <StackPanel>
            <StackPanel Orientation="Horizontal" Margin="3 0 0 0">
                <Button Name="btnBasket" Content="Basketbol Topu" Margin="5" Padding="5" Click="btnBasket_Click"    />
                <Button x:Name="btnFutbol" Content="Futbol Topu" Margin="5"  Padding="5" Click="btnFutbol_Click"/>
                <Button x:Name="btnVoleybol" Content="Voleybol Topu" Margin="5"  Padding="5" Click="btnVoleybol_Click"/>

            </StackPanel>
            <Image Margin="15" 
                   Name="imgTop"
               Source="/resimler/basketbolTopu.jpg" 
               Stretch="Uniform"/>
        </StackPanel>
        
        

    </Grid>
</Window>

```


**C# kodları**
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

        private void btnBasket_Click(object sender, RoutedEventArgs e)
        {
            imgTop.Source = new BitmapImage(new Uri("/resimler/basketbolTopu.jpg", UriKind.Relative));
        }

        private void btnFutbol_Click(object sender, RoutedEventArgs e)
        {
            imgTop.Source= new BitmapImage(new Uri("/resimler/futbolTopu.jpg", UriKind.Relative));
        }

        private void btnVoleybol_Click(object sender, RoutedEventArgs e)
        {
            imgTop.Source = new BitmapImage(new Uri("/resimler/voleybolTopu.jpg", UriKind.Relative));
        }
    }
}

```
