
### Örnek Uygulama (Label, Textbox, Button ve Listbox kullanımı) ###
>  Aşağıdaki Uygulamada Toolbox'dan (Araç Kutusu) Label, TextBox, Button ve ListBox kontrolleri sürekle bırak yöntemi ile MainWindow'a eklenmiştir.



![image](https://user-images.githubusercontent.com/28144917/152680886-fbe1f05e-63ca-4684-9036-e3e0cb326e8a.png)

```xml
<Window x:Class="WpfApp1.IlkUygulama"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp1"
        mc:Ignorable="d"
        Title="IlkUygulama" Height="301" Width="556">
    <Grid>
        <Label x:Name="label" 
               Content="Ad Soyad" 
               HorizontalAlignment="Left"
               Height="33" 
               Margin="41,46,0,0" 
               VerticalAlignment="Top" 
               Width="160"/>
            
        <TextBox x:Name="textBox" 
                 HorizontalAlignment="Left" 
                 Height="33" 
                 Margin="121,46,0,0" 
                 TextWrapping="Wrap" 
                 VerticalAlignment="Top" 
                 Width="167"/>
            
        <Button x:Name="button" 
                Content="Listeye Ekle" 
                HorizontalAlignment="Left" 
                Height="33" Margin="312,46,0,0" 
                VerticalAlignment="Top" 
                Width="186"/>
            
        <ListBox x:Name="listBox" 
                 HorizontalAlignment="Left" 
                 Height="128" 
                 Margin="41,106,0,0" 
                 VerticalAlignment="Top" 
                 Width="457" />

    </Grid>
</Window>
```
**Not:** Ekrandaki nesneler XAML yapısında  mantıksal bir ağaç şeklinde bulunurlar. Yukarıdaki örneği incelersek kök olarak Window onun içinde bir Grid ve Grid'in içerisinde de Label, Textbox, Button ve ListBox nesneleri bulunmaktadır.

> Herhangi bir kontrolün(nesnenin) özelliklerin değiştirmek ve olayları(Event) ile ilgili düzenleme yapmak için nesne seçiliyken aşağıdaki özellikler(Properties) penceresinden yararlanılabilir. Ya da direk XAML kodları üzerinden de bu işlem yapılabilir.

| Özellikler |Olaylar|
|:--------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/152681894-52f66a26-cbbf-44d0-9049-579d63543aad.png)       |![image](https://user-images.githubusercontent.com/28144917/152682028-6bbdcc32-2fdd-435f-ba6f-629158f61da7.png)| 

> Butona'a tıklama olayı eklendikten sonra Button'umuzun XAML kodu aşağıdaki gibi olmuştur.

```XAML
<Button x:Name="button1" 
                Content="Listeye Ekle" 
                HorizontalAlignment="Left" 
                Height="33" Margin="312,46,0,0" 
                VerticalAlignment="Top" 
                Width="186" 
                Click="ListeyeEkleClick"/>
```

> Tasarımın  c# kod kısmı aşağıdaki gibi görünmektedir.

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
using System.Windows.Shapes;

namespace WpfApp1
{
    /// <summary>
    /// IlkUygulama.xaml etkileşim mantığı
    /// </summary>
    public partial class IlkUygulama : Window
    {
        public IlkUygulama()
        {
            InitializeComponent();
        }

        private void ListeyeEkleClick(object sender, RoutedEventArgs e)
        {

        }
    }
}

```


> Uygulamadda TextBox'a girilen Ad Soyad bilgisinin ListBox'a ekletilebilmesi için ListeyeEkleClick metodu içerisine aşağıdaki kodların eklenmesi gerekir


```csharp
        private void ListeyeEkleClick(object sender, RoutedEventArgs e)
        {
            listBox.Items.Add(textBox1.Text);   
        }
```


> Uygulamanın Son çalışır hali aşağıdadır.

![image](https://user-images.githubusercontent.com/28144917/152682615-8540ff67-3e88-40ae-aae9-5a28a54eabd6.png)
