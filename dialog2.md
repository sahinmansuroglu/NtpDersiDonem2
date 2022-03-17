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
            OpenFileDialog openFileDialog = new OpenFileDialog();
            if (openFileDialog.ShowDialog() == true)
            {

                TextEditor.Text = File.ReadAllText(openFileDialog.FileName);
            }
        }
    }
```
