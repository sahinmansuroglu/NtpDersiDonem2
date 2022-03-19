## SaveFileDialog ##

![image](https://user-images.githubusercontent.com/28144917/159107268-a50cb393-6a78-4406-b62f-befaa8a6bb4b.png)


```xaml
Grid Margin="10">
        <Grid.RowDefinitions>
            <RowDefinition Height="30"></RowDefinition>
            <RowDefinition Height="*"></RowDefinition>
        </Grid.RowDefinitions>

        <StackPanel Orientation="Horizontal"
                    HorizontalAlignment="Center"
                    Grid.Row="0">
            
            <Button Name="btnDosyaAc" 
                    VerticalAlignment="Center"
                    Click="btnDosyaAc_Click"
                    Content="Dosya Aç"
                    Margin="0 0 10 0"/>
            
            <Button Name="btnDosyayaKaydet" 
                    VerticalAlignment="Center"
                    Click="btnDosyayaKaydet_Click"
                    Content="Dosyaya Kaydet"/>
            
        </StackPanel>
        
        <TextBox Name="TextEditor" 
                 Grid.Row="1" />
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
            OpenFileDialog openFileDialog = new OpenFileDialog();
            if (openFileDialog.ShowDialog() == true)
            {

                TextEditor.Text = File.ReadAllText(openFileDialog.FileName);
            }
        }

        private void btnDosyayaKaydet_Click(object sender, RoutedEventArgs e)
        {
            SaveFileDialog saveFileDialog = new SaveFileDialog();
            saveFileDialog.Filter = "Text files (*.txt)|*.txt|All files (*.*)|*.*";
            if (saveFileDialog.ShowDialog() == true)
            {
                   File.WriteAllText(saveFileDialog.FileName, TextEditor.Text);
            }
        }
    }
```


