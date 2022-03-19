## OpenFileDialog ##

![image](https://user-images.githubusercontent.com/28144917/158810785-5dc1a646-e177-4284-b228-8be10d58f4cb.png)

```xaml
 <Grid Margin="10">
        <Grid.RowDefinitions>
            <RowDefinition Height="30"></RowDefinition>
            <RowDefinition Height="*"></RowDefinition>
        </Grid.RowDefinitions>
        
        <Button Name="btnDosyaAc" 
                Grid.Row="0"
                HorizontalAlignment="Center" 
                VerticalAlignment="Center"
                Click="btnDosyaAc_Click"
                Content="Dosya Aç"
        />
        <TextBox Name="TextEditor" 
                 Grid.Row="1"
        />
    </Grid>
```


```csharp
public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }
        
        private void btnDosyaAc_Click(object sender, RoutedEventArgs e)
        {
           //using Microsoft.Win32; ad uzayı eklenmeli
            OpenFileDialog openFileDialog = new OpenFileDialog();
            if (openFileDialog.ShowDialog() == true)
            {
                //using System.IO; ad uzayı eklenmeli
                TextEditor.Text = File.ReadAllText(openFileDialog.FileName);
            }
        }
    }
```


```csharp
private void OpenFileButton_Click(object sender, RoutedEventArgs e)
        {
            OpenFileDialog openFileDialog = new OpenFileDialog();
         
            //Varsayılan olarak belgelerim klasörünü gösterebilmek için aşağıdaki kod kullanılır
            //openFileDialog.InitialDirectory = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments);
            //Varsayılan olarak masaüstünü klasörünü gösterebilmek için aşağıdaki kod kullanılır
            //openFileDialog.InitialDirectory = Environment.GetFolderPath(Environment.SpecialFolder.Desktop);

            ///Varsayılan olarak diskin C Bölümünügösterebilmek için aşağıdaki kod kullanılır
            //openFileDialog.InitialDirectory = @"C:\";

           // Bulunulan Klasörden 3 Aşama Yukarıdaki klasörü gösterebilmek için kullanılır
            openFileDialog.InitialDirectory = Path.GetFullPath(Environment.CurrentDirectory + @"\..\..\..");

            // Dosya aç menüsü ile açılabilecek dosya uzantılarını istenilirse ayalanabilir.
            //Text Dosyaları(*.txt)|*.txt
            //Resim Dosyaları (*.png;*.jpeg)|*.png;*.jpeg|All files (*.*)|*.*"
            openFileDialog.Filter = "Text files (*.txt)|*.txt|All files (*.*)|*.*";
            if (openFileDialog.ShowDialog() == true)
            {
                TextEditor.Text = File.ReadAllText(openFileDialog.FileName);
            }
```
