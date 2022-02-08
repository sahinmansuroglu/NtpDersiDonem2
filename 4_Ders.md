## Wpf nesnelerinin Ortak Özellikleri ile ilgili Örnek ##
> Aşağıda verilenleri yeni bir WPF uygulaması açarak sirası ile gerçekleşitiriniz.

    1. Ana Pencereni genişliğini 500px yükseliğini de 400px
    2. Boş bir Grid Oluşturunuz.
    3. Oluşturulan gridin arka plan rengini "Chocolate" olarak ayarlayın.
    4. Oluşturulan grid'in ana pencere ile arasındaki boşluğu 15 pixel olarak ayarlayınız.
    5. Grid içerisinde grid ile arasındaki boşluk 10 olacak şekilde bir border nesnesi oluşturunuz. 
    6. Oluşturulan  border'a alt ve üst kalınlığı 2 px  sol ve sağ kalınlığı 4 px  ve rengi "red" olan bir kenarlık ekletin.
    7. Oluşturulan border'a CornerRadius ile 15 px'lik bir köşe yumuşatma yapınız.
    8. Oluşturulan border içerisine boş bir grid oluşturunuz.
    9. Oluşturulan grid'in içerisinde
    
	a. Sol Üst Köşeye label ekleyin 
		(İçeriği "Galatasaray" arkaplan rengi "red" ön plan rengi "yellow" olacak  )
	b. Sağ Üst Köşeye label ekleyin 
		(İçeriği "Fenerbahçe" arkaplan rengi "blue" ön plan rengi "yellow" olacak )
	c. Sol alt Köşeye label ekleyin 
		(İçeriği "Anadolu Efes" arkaplan rengi "blue" ön plan rengi "white" olacak  )
	d. Sağ alt Köşeye label ekleyin 
		(İçeriği "Beşiktaş" arkaplan rengi "black" ön plan rengi "white" olacak   )
	e. Tüm Labellerin genişiği 100px yüksekliği 40px ve içerisindeki yazılar dikeyde ve yatayda ortalı olacak.
	f. Tüm labelleri köşelerden 15px uzaklıkta olacak.
	
    10. Gridin ortasında 70px genişliğinde ve 70 px yükseliğinde içeriği "Tıklayınız." olan bir buton ekleyin.
    11. Buton Seçili iken properties/event bölümünden "click" olayına "tiklanmaMetodu" adinda bir metod ekleyin. 
    12. Butona tıklandığında ekrana message box içerisinde "Merhaba WPF Uygulaması" yazdırın.

> **Uygulamanın istenilen ekran görüntüsü**

![image](https://user-images.githubusercontent.com/28144917/152936876-d61e6a25-f7e6-4901-aa6d-e5668435cd23.png)


#### Uygulamanın XAML kodları ####

```xaml
<Window x:Class="WpfApp14.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp14"
        mc:Ignorable="d"
        Title="MainWindow" Height="500" Width="400">
    <Grid Background="Chocolate"  Margin="15" >
        <Border Margin="10"
                BorderThickness="4 2 4 2"
                BorderBrush="Red"
                CornerRadius="15">
           
	   <Grid Margin="15">
                
                <Label
                    	VerticalContentAlignment="Center"
                    	HorizontalContentAlignment="Center"
                    	Width="100"
                    	Height="40"
                    	VerticalAlignment="Top"
                   	HorizontalAlignment="Left"
                   	Content="Galatasaray"
                    	Background="Red"
                    	Foreground="Yellow"/>
			
                <Label 
			VerticalAlignment="Top"
                   	HorizontalAlignment="Right"
                   	Content="Fenerbahçe"
                    	Width="100"
                    	Height="40"
                        Background="Blue"
                    	Foreground="Yellow"
                        VerticalContentAlignment="Center"
                    	HorizontalContentAlignment="Center"/>
			
                <Label 
			VerticalAlignment="Bottom"
                   	HorizontalAlignment="Right"
                   	Content="Beşiktaş"
                        Width="100"
                    	Height="40"
                        Background="Black"
                    	Foreground="White"
                        VerticalContentAlignment="Center"
                    	HorizontalContentAlignment="Center"/>
                
		<Label VerticalAlignment="Bottom"
                   	HorizontalAlignment="Left"
                   	Content="Anadolu Efes"
                    	Width="100"
                    	Height="40"
                        Background="Blue"
                    	Foreground="White"
                       VerticalContentAlignment="Center"
                    	HorizontalContentAlignment="Center"/>
			
                <Button 
                    	Width="70" 
                    	Height="70" 
                    	Content="Tıklayınız."
                    	Click="tiklamaMetodu"/>



            </Grid>
        </Border>
    </Grid>
</Window>

```
