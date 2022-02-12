## WPF (Windows Presentation Foundation) Nedir ##
> WPF, grafik tabanlı kullanıcı arayüzleri yaratmak için kullanılan bir UI(User Interface) framework'üdür. WPF, .Net ailesinin bir üyesidir ve bundan dolayı  .NET framework'ünün bir parçası olarak çalışacağı sisteme kurulur. Visual Studio IDE ile geliştirilir.

> WPF uygulamalarında kullanıcı arayüzü oluşturmak için XAML (Extensible Application Markup Language) kullanılır. XAML, WPF'in kullanıcı arayüzü geliştirmek için kullandığı script dilinin adıdır. C# ise WPF'in arka planında kullanılan programlama dilidir.(WPF'in arka planında Visual basic programlama dili ile de geliştirme yapılabilir)

### İlk Uygulama ###
> Aşağıdaki ilk Uygulamamızda Ana Penceremizin(Window) içerisinde bir Label nesnesi kullandık ve ekranda "Merhaba WPF Uygulaması" mesajını yazdırdık.

```xml
<Window x:Class="WpfApp1.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp1"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <Grid>
        <Label HorizontalAlignment="Center" VerticalAlignment="Center" FontSize="65">
            Merhaba WPF Uygulaması
        </Label>
        
       
    </Grid>
</Window>
```

**Ekran Çıktısı**

![image](https://user-images.githubusercontent.com/28144917/152687981-3f973733-4009-420e-a724-0a3d70dbcd7e.png)

**Window Nesnesinin önemli özellikleri**
> **Icon:** Pencerenin Sol üst köşesinde ve pencere başılığının solunda  gösterilen pencere simgesini tanımlamamızı sağlar.

> **ResizeMode:**
Bu, son kullanıcının pencerenizi yeniden boyutlandırıp boyutlandıramayacağını kontrol eder. Varsayılan, CanResize'dır; bu, kullanıcının pencereyi  yeniden boyutlandırmasına imkan verir. CanMinimize, kullanıcının pencereyi simge durumuna küçültmesine izin verir, ancak ekranı büyütmesine veya büyütüp küçültmesine izin vermez. NoResize, büyütme ve küçültme düğmelerinin kaldırıldığı bir seçenektir.

> **ShowInTaskbar:**
 Varsayılan değer True, ancak false olarak ayarlarsanız pencereniz Windows görev çubuğunda gösterilmez. 

> **SizeToContent:**
Bu özellik pencerenin,  içeriğine uyacak şekilde kendisiniotomatik olarak yeniden boyutlandırabilmesi için kullanılır. Varsayılan, Manuel'dir; bu, pencerenin otomatik olarak yeniden boyutlandırılmadığı anlamına gelir. Diğer seçenekler Width, Height ve WidthAndHeight'tır ve bunların her biri pencere boyutunu otomatik olarak yatay, dikey veya her iki şekilde ayarlayacaktır.

> **Topmost:**
Varsayılan false'dur, ancak true olarak ayarlanırsa, Pencereniz simge durumuna küçültülmediği sürece diğer pencerelerin üstünde kalacaktır.

> **WindowStartupLocation:**

Pencerenizin ilk konumunu kontrol eder. Varsayılan, Manuel'dir; bu, pencerenin başlangıçta pencerenizin Üst ve Sol özelliklerine göre konumlandırılacağı anlamına gelir. Diğer seçenekler, pencereyi sahip penceresinin ortasına konumlandıran CenterOwner ve pencereyi ekranın ortasına konumlandıran CenterScreen'dir.

> **WindowState :**
Pencerenin İlk ekrana gelme durumunu kontrol eder. Normal, Maksimize veya Minimize olabilir. 
