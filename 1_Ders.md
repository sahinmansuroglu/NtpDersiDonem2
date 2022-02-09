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
