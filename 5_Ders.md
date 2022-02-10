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

#### Button Örneği ####
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
> İki yada daha çok seçenek içerisinden seçin yapabilmek için kullanılan UI nesnesidir.

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|||
|||

**XAML kodları**

```xaml

```


**C# kodları**
```csharp

```
### 6. ComboBox  ### 
> Aşağıya doğru açılır liste oluşturmak için kullanılan UI nesnesidir

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|||
|||


**XAML kodları**

```xaml

```


**C# kodları**
```csharp

```
### 7. ListBox  ### 
> Verileri liste halinde görüntülemek için kullanılan UI nesnesidir.

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|||
|||


**XAML kodları**

```xaml

```


**C# kodları**
```csharp

```
### 8. Image  ### 
> Resim görüntülemek için kullanılan UI nesnesidir.

| Örnek Kod |Ekran Görüntüsü|
|:--------:|:----------------------------:|
|||
|||


**XAML kodları**

```xaml

```


**C# kodları**
```csharp

```
