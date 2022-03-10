 ### 2- Data Trigger ###
> Bu tetikleyici türü ```<DataTrigger>``` etiketleri arasına yazılır. Seçilen herhangi bir UI nesnesinin istenilen bir özelliği değiştiğinde tetiklenir.


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
      
            <Style TargetType="StackPanel" x:Key="stackPanelStil">
                 <Setter Property="IsEnabled"  Value = "True"/>
                 <Style.Triggers>
                     <DataTrigger Binding = "{Binding ElementName=rbBekar, Path = IsChecked}"    Value = "true">
                             <Setter Property="IsEnabled"  Value = "False"/>
                             <Setter Property="Background"  Value = "LightGray"/>
                 </Style.Triggers>
            </Style>

    </Window.Resources>

    <StackPanel Margin="10">
        
       <StackPanel Orientation="Horizontal">
            <Label Content="Evlilik Durumu:" FontWeight="Bold"/>
            <RadioButton x:Name="rbEvli" Content="Evli :" FontWeight="Bold" IsChecked="True"/>
            <RadioButton x:Name="rbBekar" Content="Bekar :" FontWeight="Bold"/>
        </StackPanel>

        <StackPanel Orientation="Horizontal" Style="{StaticResource stackPanelStil}" >
            <Label Content="Eşinin Mesleği" FontWeight="Bold"/>
            <TextBox Width="100" />
        </StackPanel>

    </StackPanel>
    
</Window>

```
> Aynı uygulama istenirse aşağıdaki gibi stackPanel için ayrı bir stil tanımlayarak da gerçekleşitirilebilir.
 
 ```xaml
 <Window x:Class="WpfApp36.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp36"
        mc:Ignorable="d"
        Title="MainWindow" Height="200" Width="300">
    <Window.Resources>
        <Style TargetType="StackPanel" x:Key="StackPanelStil">
            <Setter  Property="IsEnabled" Value="False"/>
            <Setter  Property="Background" Value="LightGray"/>
            <Style.Triggers>
                <DataTrigger   Binding = "{Binding ElementName=rbEvli, Path = IsChecked}"     Value = "true">
                    <Setter  Property="IsEnabled" Value="True"/>
                    <Setter  Property="Background" Value="Transparent"/>
                </DataTrigger>

                
            </Style.Triggers>
        </Style>

    </Window.Resources>
    <StackPanel Margin="10">
        <StackPanel Orientation="Horizontal">

            <Label Content="Evlilik Durumu:" FontWeight="Bold"/>
            <RadioButton x:Name="rbEvli" Content="Evli :" FontWeight="Bold" IsChecked="True"/>
            <RadioButton x:Name="rbBekar" Content="Bekar :" FontWeight="Bold"/>

        </StackPanel>

        <StackPanel Orientation="Horizontal" Style="{StaticResource StackPanelStil}" >
            <Label Content="Eşinin Mesleği" FontWeight="Bold"/>
            <TextBox Width="100">
            </TextBox>

        </StackPanel>

    </StackPanel>
</Window>

 ```
