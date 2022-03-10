### 3- Event Trigger ###
> Bu tetikleyici türü <EventTrigger> etiketleri arasına yazılır. Seçilen herhangi bir UI nesnesi üzerinde bir olay(event) gerçekleştiğinde meydana gelir. Genellikle bir animasyonlarla beraber kullanılır.
    
> Aşağıdaki Örnekte  verilen stili kullanan bir butonun mouse ile üzerine gelindiğinde yazı boyutu animasyonlu bir şekilde  28 olmuştur.
    
```xaml    
    <Style  TargetType="Button">
            <Setter Property = "Foreground" Value = "Red"/>
            <Setter Property = "FontWeight" Value = "Bold" />
            <Setter Property = "FontSize" Value = "15" />
            <Setter Property = "Width" Value = "100" />
            <Style.Triggers>
                <EventTrigger RoutedEvent="MouseEnter">
                    <EventTrigger.Actions>
                        <BeginStoryboard>
                            <Storyboard>
                                <DoubleAnimation Duration="0:0:0.300" Storyboard.TargetProperty="FontSize" To="28" />
                                <DoubleAnimation Duration="0:0:0.300" Storyboard.TargetProperty="Width" To="200" />
                            </Storyboard>
                        </BeginStoryboard>
                    </EventTrigger.Actions>
                </EventTrigger>
               
            </Style.Triggers>
        </Style>
```
    > Uygulamanın Tamamlanmış Hali aşağıdadır.
    
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
       

        <Style  TargetType="Button">
            <Setter Property = "Foreground" Value = "Red"/>
            <Setter Property = "FontWeight" Value = "Bold" />
             <Setter Property = "FontSize" Value = "15" />
            <Setter Property = "Width" Value = "100" />
            <Style.Triggers>
                <EventTrigger RoutedEvent="MouseEnter">
                    <EventTrigger.Actions>
                        <BeginStoryboard>
                            <Storyboard>
                                <DoubleAnimation Duration="0:0:0.300" Storyboard.TargetProperty="FontSize" To="28" />
                                   <DoubleAnimation Duration="0:0:0.300" Storyboard.TargetProperty="Width" To="200" />
                            </Storyboard>
                        </BeginStoryboard>
                    </EventTrigger.Actions>
                </EventTrigger>
               
            </Style.Triggers>
        </Style>

    </Window.Resources>
    <StackPanel Margin="10">
        <Button Content="Tıklayınız">
            
        </Button>

    </StackPanel>
</Window>
 
```
    
#### Örnek-1 ####
> Yukarıdaki örnekte mouse ile butonun üzerine gelindiğinde yazı boyutu 28 olmuştur ancak tekrar eski haline dönmemiştir. Yukarıdaki uygulamaya <EventTrigger RoutedEvent="MouseLeave"> triggeri ekleyerek butonun üzerinden ayrılındığında yazı boyutu animasyonlu bir şekilde tekrar eski haline gelsin.
 
    
**Çözüm**
    
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
       

        <Style  TargetType="Button">
            <Setter Property = "Foreground" Value = "Red"/>
            <Setter Property = "FontWeight" Value = "Bold" />
            <Setter Property = "FontSize" Value = "15" />
            <Style.Triggers>
                <EventTrigger RoutedEvent="MouseEnter">
                    <EventTrigger.Actions>
                        <BeginStoryboard>
                            <Storyboard>
                                <DoubleAnimation Duration="0:0:0.300" Storyboard.TargetProperty="FontSize" To="28" />
                            </Storyboard>
                        </BeginStoryboard>
                    </EventTrigger.Actions>
                </EventTrigger>
                <EventTrigger RoutedEvent="MouseLeave">
                    <EventTrigger.Actions>
                        <BeginStoryboard>
                            <Storyboard>
                                <DoubleAnimation Duration="0:0:0.800" Storyboard.TargetProperty="FontSize" To="15" />
                            </Storyboard>
                        </BeginStoryboard>
                    </EventTrigger.Actions>
                </EventTrigger>
            </Style.Triggers>
        </Style>

    </Window.Resources>
    <StackPanel Margin="10">
        <Button Content="Tıklayınız">
            
        </Button>

    </StackPanel>
</Window>
```
#### Örnek-2 ####
> Aşağıdaki örnekte bir textboxa odaklanıldığında odaklanılan textboxun arkaplan rengi animasyonlu bir şekilde "LightPink" rengine odak kaybeldiğinde ise tekrar eski hali olan "LightGray" rengine döndürelecektir. 
    <table>
        <tr>
            <td>![image](https://user-images.githubusercontent.com/28144917/157028743-c16ee0c1-b1fc-402c-8a6c-80aa283aad95.png)</td>
            <td>![image](https://user-images.githubusercontent.com/28144917/157028814-d6fbc9dc-5e5d-4e5a-b03e-c38eca625334.png)</td>
        </tr>
        </table>
    
> Kullanılacak Olan EventTrigger'lar
    
    1- Textbox'a odaklanıldığında çalışması gereken trigger: <EventTrigger RoutedEvent="GotFocus">
    2- Textbox'daki odaklanma kaybolduğu zaman  çalışması gereken trigger: <EventTrigger RoutedEvent="LostFocus">
    
**Çözüm** 
    
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
       

        <Style  TargetType="Button">
            <Setter Property = "Foreground" Value = "Red"/>
            <Setter Property = "FontWeight" Value = "Bold" />
            <Setter Property = "FontSize" Value = "15" />
            <Setter Property = "Margin" Value = "10" />
            <Setter Property = "Padding" Value = "5" />
            
        </Style>
        <Style  TargetType="TextBox">
            <Setter Property = "Foreground" Value = "DarkSlateGray"/>
            <Setter Property = "Background" Value = "LightGray"/>
            <Setter Property = "FontWeight" Value = "Bold" />
            <Setter Property = "FontSize" Value = "15" />
            <Setter Property = "Padding" Value = "2" />
            <Setter Property = "Margin" Value = "10" />
            <Style.Triggers>
                <EventTrigger RoutedEvent="GotFocus">
                    <BeginStoryboard>
                        <Storyboard>
                            <ColorAnimation 
                                Storyboard.TargetProperty="Background.Color"
                                To="LightPink" Duration="0:0:0.25"/>
                        </Storyboard>
                    </BeginStoryboard>
                </EventTrigger>

                <EventTrigger RoutedEvent="LostFocus">
                    <BeginStoryboard>
                        <Storyboard>
                            <ColorAnimation 
                                Storyboard.TargetProperty="Background.Color"
                                To="LightGray" Duration="0:0:0.25"/>
                        </Storyboard>
                    </BeginStoryboard>
                </EventTrigger>
            </Style.Triggers>
        </Style>

        

    </Window.Resources>
    
    <StackPanel Margin="10">
        <StackPanel>
            <Label Content="Ad" />
            <TextBox />
            <Label Content="Soyad" />
            <TextBox/>
            <Label Content="Doğum Yeri" />
            <TextBox/>

            <StackPanel Orientation="Horizontal" HorizontalAlignment="Right">
                <Button>Tamam </Button>
                <Button>İptal</Button>
            </StackPanel>
        </StackPanel>

    </StackPanel>
</Window>
  
```
