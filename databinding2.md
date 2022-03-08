## DataContext Kullanımı ##

> Datacontext özelliği, verileri kullanıcı arayüzüne bağlamak için kullanılır. 



>Örneğin elimizde aşağıdaki gibi bir Ogrenci sınıfı, bu sınıftan türetilen bir ogrenci nesnesi ve bu nesneyi bağlamak istediğimiz bir kullanıcı arayüzü olsun. 


| Ogrenci Class'ı |Ogrenci Nesnesi|Kullanıcı Arayüzü|
|:--------:|:----------------------------:|:----------------------------:|
|![image](https://user-images.githubusercontent.com/28144917/157192461-da851809-58df-4a41-ae13-8cd35d717232.png)|![image](https://user-images.githubusercontent.com/28144917/157192574-c4746eb6-0b0d-4225-8efc-1df0ef761456.png)|![image](https://user-images.githubusercontent.com/28144917/157192248-3a1fb4f0-9d52-4c50-abe9-963edc1a1bd9.png)|

 > Oluşturulan nesneyi kullanıcı arayüzüne bağlayabilmek için   DataContext özelliğinden faydalanılır. Bunun için ogrenci nesnesi, kullanıcı arayuzunu içeren gridPanel, stackPanel veya Window gibi UI nesnelerinin dataContext özelliğine  atanır. (Bu atamayı C# tarafında yapacağız)


> Xaml kodları verilen Kullanıcı arayüzü ile ogrenci nesnemizi bağlayabilmek için MainWindow'umuz oluşturulurken aşağıdaki gibi bağlama işlemi sağlayabiliriz.
```csharp
       public MainWindow()
        {
            InitializeComponent();
            
            this.DataContext = ogrenci; //(Burada this Window'u işaret eder)
                     yada
            stackPanel1.DataContext = ogrenci;

        }
```


```xaml
<Window x:Class="WpfApp7.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp7"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="300">

    <Window.Resources>
        <Style TargetType="TextBox">
            <Setter Property="Margin" Value="5"/>
        </Style>
    </Window.Resources>
    
  <StackPanel Margin="1" Name="stackPanel1" >
        
            <Label Content="Ad " />
            <TextBox Name="txtAd" Text="{Binding Path=Ad}" />
            <Label Content="Soyad " />
        <TextBox Name="txtSoyad" Text="{Binding Path=Soyad}" />


        <Button Click="Button_Click"  >
            Tıklayınız
        </Button>



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

namespace WpfApp7
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {

        Ogrenci ogrenci = new Ogrenci
        {
            Ad = "Ayhan",
            Soyad = "AŞKIN"
        };
        public MainWindow()
        {
            InitializeComponent();
            
            this.DataContext = ogrenci;    
            //stackPanel1.DataContext = ogrenci; // bu şekilde de atama yapılabilir
        }

      

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show($"{ogrenci.Ad} {ogrenci.Soyad}")
        }

       
    }
    class Ogrenci
    {
        public string Ad { get; set; }
        public string Soyad { get; set; }
    }

}
```
> Uygulama çalışıtırıldığında aşağıdaki gibi görülecektir. Arayüzde ad veya soyad değişitirildiğinde bağlı olduğu nesnedeki property'ler de güncellenecektir.

|![image](https://user-images.githubusercontent.com/28144917/157226044-7f1c7e22-afc5-43bb-8327-4d2114307e2e.png)|![image](https://user-images.githubusercontent.com/28144917/157226165-7ed4f2a6-295e-48de-823b-a20db4dd7ece.png)|


> Aşağıdaki çıktının nedenin açıklayınız..


|![image](https://user-images.githubusercontent.com/28144917/157229731-ca1f7b90-69b0-4fca-a8fd-427d4a39c549.png)|![image](https://user-images.githubusercontent.com/28144917/157229659-a0a92f56-fb2e-4ff0-9b21-b8f7eb85e3c2.png)|
