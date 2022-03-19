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
            //TODO: Step 2: Show students how they can set the InitialDirectory
            //by making use of "SpecialFolders" such as MyDocuments, Desktop, etc
            //They don't need to specify the speicif folder path since it's defined in
            //the Environment class 
            //openFileDialog.InitialDirectory = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments);
            //openFileDialog.InitialDirectory = Environment.GetFolderPath(Environment.SpecialFolder.Desktop);

            //TODO: Step 3: Show that they can use absolute paths
            //openFileDialog.InitialDirectory = @"C:\";

            //TODO: Step 4: Show that they can use relative paths
            //In this example we go 3 levels up the folder hierachy
            openFileDialog.InitialDirectory = Path.GetFullPath(Environment.CurrentDirectory + @"\..\..\..");

            //TODO: Step 5: Add an openFileDialog.Filter
            //Show student that they can filter the dialog box to only use images
            //Text files and so on
            //Custom file (*.cus)|*.cus
            //Text files (*.txt)|*.txt
            //"Image files (*.png;*.jpeg)|*.png;*.jpeg|All files (*.*)|*.*"
            openFileDialog.Filter = "Text files (*.txt)|*.txt|All files (*.*)|*.*";
            if (openFileDialog.ShowDialog() == true)
            {
                TextEditor.Text = File.ReadAllText(openFileDialog.FileName);
            }
```
