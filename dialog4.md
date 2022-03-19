## PrintDialog ##

![image](https://user-images.githubusercontent.com/28144917/159107623-17a9ef32-3fa1-410b-8338-24e73653b7cf.png)

```xaml
<Grid Margin="10" x:Name="grid1">
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
                    Content="Dosyaya Kaydet"
                    Margin="0 0 10 0"/>
            
            <Button Name="btnYazdır" 
                    VerticalAlignment="Center"
                    Click="btnYazdır_Click"
                    Content="Yazdır"/>

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

        private void btnYazdır_Click(object sender, RoutedEventArgs e)
        {
            PrintDialog printDialog = new PrintDialog();


            if (printDialog.ShowDialog() == true)

            {
                // printDialog.PrintVisual(TextEditor, "Metin Yazdırılıyor");
                printDialog.PrintVisual(grid1, "Metin Yazdırılıyor");
            }

        }
    }

```

> FlowDocument ile bir belge oluşuturulup bu belge   printDialog.PrintDocument ile yazdırılabilir

![image](https://user-images.githubusercontent.com/28144917/159107952-a11e2a42-2cb3-4775-90a5-24eb4874a19e.png)

```xaml
 <Grid Margin="10" x:Name="grid1">
        <Grid.RowDefinitions>
            <RowDefinition Height="30"></RowDefinition>
            <RowDefinition Height="*"></RowDefinition>
        </Grid.RowDefinitions>

        <Button Name="btnYazdır" 
                    VerticalAlignment="Center"
                    Click="btnYazdır_Click"
                    Content="Yazdır"/>

        <FlowDocumentReader Grid.Row="1">
            
            <FlowDocument Name="flowDokuman1">
                
                <Paragraph>
                    <Bold>Wpf Uygulamalarında</Bold>  Temel olarak aşağıdaki Dilaog pencereleri vardır
                </Paragraph>

                <List>
                    <ListItem>
                        <Paragraph>Mesaj Kutusu</Paragraph>
                    </ListItem>
                    
                    <ListItem>
                        <Paragraph>Dosya Aç Penceresi</Paragraph>
                    </ListItem>
                    
                    <ListItem>
                        <Paragraph>Dosya Kaydet Penceresi</Paragraph>
                    </ListItem>
                    
                    <ListItem>
                        <Paragraph>Yazdırma Penceresi</Paragraph>
                    </ListItem>
                </List>
                
            </FlowDocument>
            
        </FlowDocumentReader>
        
    </Grid>
```


```csharp
 public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }
       

        private void btnYazdır_Click(object sender, RoutedEventArgs e)
        {
            PrintDialog printDialog = new PrintDialog();


            if (printDialog.ShowDialog() == true)

            {
                printDialog.PrintDocument(((IDocumentPaginatorSource)flowDokuman1).DocumentPaginator, "Döküman Yazdırılıyor");
               
            }

        }
    }
```


