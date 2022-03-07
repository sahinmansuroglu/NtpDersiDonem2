## Trigger (Tetikleyici ) nedir?

> Trigger'lar temel olarak istenilen bir event (olay) gerçekleştiğinde belirlenen UI nesnelerinin property’lerini değiştirebilmemize olanak sağlar. Trigger'lar genellikle bir stil içersinde tanımlanırlar
> Üç Çeşit trigger yapısı bulunmaktadır Bunlar;

    1-Property trigger 
    2-Data Trigger 
    3-Event trigger 
 
 ### 1- Property Trigger ###
 > En yaygın kullanılan tetikleyici türü Property Trigger'dır ve <Trigger></trigger> tagları arasına tanımlanırlar.  Bu tetikleyici türü ile her hangi bir UI nesnesinin istenilen bir özelliğinini değişmesini yine aynı nesnenin başka bir özelliğinin istenilen bir değere ulaşmasına göre sağlıyabilirz.
    

> Aşağıda tanımlanan stil içerisinden bir trigger tanımlanmıştır. Bu trigger "IsMouseOver" property'si "true" olduğunda tetiklenerek "foregorund" property'sini red yapmıştır. Yani  bu stile sahip bir butonun üzerine mouse ikonunu getirdiğimizde yazı rengi kırmızı olmuştur.

```xaml

        <Style x:Key = "ButonStil" TargetType = "Button">
            <Setter Property = "Foreground" Value = "Blue" />
            <Setter Property = "FontSize" Value = "15" />
            <Style.Triggers>
                <Trigger Property = "IsMouseOver" Value = "True">
                    <Setter Property = "Foreground" Value = "red" />
                </Trigger>
            </Style.Triggers>
        </Style>
```

> Uygulamanın tamamlanmış Hali Aşağıdadır.
    
```xaml
    <Window x:Class="WpfApp10.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp10"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <Window.Resources>

        <Style x:Key = "ButonStil" TargetType = "Button">
            <Setter Property = "Foreground" Value = "Blue" />
            <Setter Property = "FontSize" Value = "15" />
            <Style.Triggers>
                <Trigger Property = "IsMouseOver" Value = "True">
                    <Setter Property = "Foreground" Value = "red" />
                </Trigger>
            </Style.Triggers>
        </Style>
    </Window.Resources>
    
    <Grid>
        <Button  Margin="50" Style="{StaticResource ButonStil}">
            Tıklayınız
        </Button>
    </Grid>
</Window>
```


#### Örnek-1 ####
> Content'i "En Büyük İçel İdman Yurdu" olan bir label ekleyiniz. Label'in arkaplanı mavi yazı rengi kırmızı olsun. Bir Trigger oluşturarak label'in üzerine gelindiğinde yazı rengini mavi arkaplanı kırmızı olmasını sağlayınız.

**Çözüm**

```xaml
<Window x:Class="WpfApp35.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp35"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="600">
    
    
    <Window.Resources>

        <Style x:Key = "labelStil" TargetType = "Label">
            <Setter Property = "Foreground" Value = "Red" />
            <Setter Property = "Background" Value = "Blue" />
            <Setter Property = "FontSize" Value = "15" />
            <Style.Triggers>
         
                <Trigger Property = "IsMouseOver" Value = "True">

                    <Setter Property = "Foreground" Value = "Blue" />
                    <Setter Property = "Background" Value = "Red" />
                </Trigger>
                
            </Style.Triggers>
            

            
        </Style>
        
    </Window.Resources>
    
    <Border>
        <Label Margin="50" Style="{StaticResource labelStil}">
            En Büyük İçel İdman Yurdu
        </Label>

    </Border>
</Window>

```

#### Örnek-2 ####
> Aşağıdaki ekran görüntüsünü tasarlayınız. Seçili RadioButton'unun yazı rengini kırmız ve bold olarak ayarlayabilşmek için trigger oluşturunuz. ( Property = "IsChecked" Value = "True")

![image](https://user-images.githubusercontent.com/28144917/156979650-931af916-f63b-4d38-bff6-e6dcbcc8cebe.png)

**Çözüm**

```xaml
<Window x:Class="WpfApp35.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp35"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="600">
    
    
    <Window.Resources>

        <Style TargetType = "RadioButton">
            <Setter Property = "Foreground" Value = "DarkBlue" />
            <Setter Property = "Margin" Value = "5" />
            <Setter Property = "FontSize" Value = "15" />
            <Style.Triggers>
         
                <Trigger Property = "IsChecked" Value = "True">

                    <Setter Property = "Foreground" Value = "Red" />
                    <Setter Property = "FontWeight" Value = "Bold" />
                </Trigger>
                
            </Style.Triggers>
            

            
        </Style>
        <Style TargetType = "Label">
            <Setter Property = "Foreground" Value = "DarkSlateGray" />
            <Setter Property = "Margin" Value = "5" />
            <Setter Property = "FontSize" Value = "20" />
            <Setter Property = "FontWeight" Value = "Bold" />



        </Style>
    </Window.Resources>
    
    <StackPanel>
        <Label Content="En sevdiğiniz Spor Branşı Nedir?"/>
        <RadioButton  Content="Futbol"/>
        <RadioButton  Content="Basketbol"/>
        <RadioButton  Content="Voleybol"/>
        <RadioButton  Content="Futsal"/>
    </StackPanel>
</Window>

```
 ### 2- Data Trigger ###
> Bu tetikleyici türü <DataTrigger> etiketleri arasına yazılır. Seçilen herhangi bir UI nesnesinin istenilen bir özelliği değiştiğinde tetiklenir.


**Örnek**
    
>   Aşağıdaki örnekte bir Buton Stil'i içerisinde DataTrigger oluşturulmuştur. Bu buton başlangıçta pasif halde iken DataTrigger sayesinde cbOnay isimli checkbox'in IsChecked özelliği true olduğu zaman bu buton aktif hale gelmektedir.
    
```xaml
   <Style TargetType="Button">
            <Setter Property="Width"  Value = "150"/>
            <Setter Property="Margin"  Value = "10"/>
            <Setter Property="IsEnabled"  Value = "False"/>
            <Style.Triggers>
                <DataTrigger Binding = "{Binding ElementName=cbOnay, Path = IsChecked}"    Value = "true">
                    <Setter Property="IsEnabled"  Value = "True"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>

```
    
> Uygulamanın Tamamlanmış Hali aşağıdadır.
    
 ![image](https://user-images.githubusercontent.com/28144917/157011761-12c68a25-5661-43cc-b7b8-e1fc1df83cef.png)

```xaml    
    <Window x:Class="WpfApp7.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp7"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="300">



    <Window.Resources>
        <Style TargetType="Button">
            <Setter Property="Width"  Value = "150"/>
            <Setter Property="Margin"  Value = "10"/>
            <Setter Property="IsEnabled"  Value = "False"/>
            <Style.Triggers>
                <DataTrigger Binding = "{Binding ElementName=cbOnay, Path = IsChecked}"    Value = "true">
                    <Setter Property="IsEnabled"  Value = "True"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>

        <Style  TargetType="CheckBox">
            <Setter Property = "Foreground" Value = "Red"/>
            <Setter Property = "FontWeight" Value = "Bold" />
        </Style>

    </Window.Resources>
    <StackPanel Margin="10">
        <CheckBox x:Name="cbOnay" Content="Kimlik Bilgilerimin Doğruluğunu onaylıyorum"/>
        <Button Content="Onayla"/>

    </StackPanel>
</Window>

```
    
**Not:** Stil ve trigger tanımlaması istenildığı takdirde aşağıdaki gibi herhangi bir UI nesnesi içerisinde de tanımlanabilir
    
```xaml   
<Button Content="Onayla">
            <Button.Style>
                <Style>
                     <Style.Triggers>
                        <DataTrigger Binding = "{Binding ElementName=cbOnay, Path = IsChecked}"    Value = "true">
                            <Setter Property="Button.IsEnabled"  Value = "True"/>
                        </DataTrigger>
                    </Style.Triggers>
                 </Style>
            </Button.Style>
        </Button>
    
```
    
#### Örnek-1 ####
> Aşağıdaki Örnekte Evlilik durumu Evli ise Eşinin mesleğinin girileceği Texbox aktif, eğer Bekar ise bu Textbox pasif olacaktır. Bu işlem için dataTrigger kullanılacaktır.
    
![image](https://user-images.githubusercontent.com/28144917/157016044-f9594cbd-8b84-4973-abcf-d7f5d8c1fc8a.png)
    
![image](https://user-images.githubusercontent.com/28144917/157016083-1aba1bb5-fccd-44dc-9c04-abe1e7d7a79c.png)

    
```xaml
    <Window x:Class="WpfApp7.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp7"
        mc:Ignorable="d"
        Title="MainWindow" Height="112" Width="300">



    <Window.Resources>
        <Style TargetType="Button">
            <Setter Property="Width"  Value = "150"/>
            <Setter Property="Margin"  Value = "10"/>
            <Setter Property="IsEnabled"  Value = "False"/>
            
        </Style>

        <Style  TargetType="CheckBox">
            <Setter Property = "Foreground" Value = "Red"/>
            <Setter Property = "FontWeight" Value = "Bold" />
        </Style>

    </Window.Resources>
    <StackPanel Margin="10">
        <StackPanel Orientation="Horizontal">
            <Label Content="Evlilik Durumu:" FontWeight="Bold"/>
            <RadioButton x:Name="rbEvli" Content="Evli :" FontWeight="Bold" IsChecked="True"/>
            <RadioButton x:Name="rbBekar" Content="Bekar :" FontWeight="Bold"/>
            
        </StackPanel>
        <StackPanel Orientation="Horizontal" >
            <StackPanel.Style>
                <Style>
                    <Style.Triggers>
                        <DataTrigger Binding = "{Binding ElementName=rbEvli, Path = IsChecked}"    Value = "true">
                            <Setter Property="StackPanel.IsEnabled"  Value = "True"/>

                        </DataTrigger>

                        <DataTrigger Binding = "{Binding ElementName=rbBekar, Path = IsChecked}"    Value = "true">
                            <Setter Property="StackPanel.IsEnabled"  Value = "False"/>
                            <Setter Property="StackPanel.Background"  Value = "LightGray"/>
                        </DataTrigger>

                    </Style.Triggers>
                </Style>

            </StackPanel.Style>
            <Label Content="Eşinin Mesleği" FontWeight="Bold"/>
            <TextBox Width="100">
               
                
            </TextBox>

        </StackPanel>

    </StackPanel>
</Window>

```

    
