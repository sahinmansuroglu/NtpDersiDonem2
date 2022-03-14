## DataGrid ile veri bağlama ##
> DataGrid verileri tablo halinde gösterebilmek için kullanılan bir kontroldür. Listeler veya koleksiyonlar tablo halinde görüntülenmek istendiğinde DataGrid'ten faydalınabilir

>Verilen DataGrid Örneklerinde Aşağıdaki Ogrenci sınıfı kullanılacaktır.

```csharp
class Ogrenci : INotifyPropertyChanged
    {
        private string ad;
        public string Ad
        {
            get
            {

                return ad;
            }
            set
            {
                ad = value;
                OnPropertyChanged("Ad");
            }

        }
        private string soyad;
        public string Soyad
        {
            get
            {

                return soyad;
            }
            set
            {
                soyad = value;
                OnPropertyChanged("Soyad");
            }

        }

        private int yazili1;

        public int Yazili1
        {
            get { return yazili1; }
            set { 
                yazili1 = value;
                OnPropertyChanged("Ortalama");
                OnPropertyChanged("Durum");
            }
        }

        private int yazili2;

        public int Yazili2
        {
            get { return yazili2; }
            set { 
                yazili2 = value;
                OnPropertyChanged("Ortalama");
                OnPropertyChanged("Durum");

            }
        }

        public double Ortalama { 
            get {
                return (Yazili1 + Yazili2) / 2.0;
            } 
        
        }
        public string Durum
        {
            get
            {
                return Ortalama<50?"Kaldınız":"Geçtiniz";
            }

        }
        protected internal virtual void OnPropertyChanged(string propertyName)
        {
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
        }

        public event PropertyChangedEventHandler PropertyChanged;
    }
```


>    **AutoGenerateColumns=True"** özelliği ile sutunlar ve sütün başlıkları bağlanan nesnedeki property'lere göre otomatik olarak oluşturulur .

<table>
<tr>

  <th>
C# kodları 
</th>
  <th>
Arayüz Kodları/Kullanıcı Arayüzü
</th>
</tr>
<tr>
  <td>

      
```csharp
public partial class MainWindow : Window
    {
        ObservableCollection<Ogrenci> ogrenciler;
        public MainWindow()
        {
            InitializeComponent();
            ogrenciler = new ObservableCollection<Ogrenci>();
            ogrenciler.Add(new Ogrenci
            {
                Ad = "Ayhan",
                Soyad = "ERKMEN",
                Yazili1 = 66,
                Yazili2 = 55

            });
            ogrenciler.Add(new Ogrenci
            {
                Ad = "Esra",
                Soyad = "EN",
                Yazili1 = 58,
                Yazili2 = 90

            });
            ogrenciler.Add(new Ogrenci
            {
                Ad = "Alin",
                Soyad = "EREN",
                Yazili1 = 66,
                Yazili2 = 10

            });
            dataGrid1.ItemsSource = ogrenciler;
        }
    }
```

</td>
  <td>

        
      
```xaml
    <Grid Margin="20">
        <DataGrid x:Name="dataGrid1"
                  AutoGenerateColumns="True"/>

    </Grid>
```
    
![image](https://user-images.githubusercontent.com/28144917/158160798-e8afdf4f-7401-49f1-ba48-48cfadfc9151.png)


</td>
</tr>
  
  
</table>

>    **AutoGenerateColumns=False"** özelliği ile sutunların bağlı oldukları property'ler ve sütün başlıkları aşağıdaki gibi manuel olarak oluşturulabilir.

    
<table>
<tr>
<th>
Arayüz Kodları
</th>
<th>
Kullanıcı Arayüzü
</th>
</tr>
<tr>
<td>

```xaml
    
    <Grid Margin="20">
        <DataGrid x:Name="dataGrid1" AutoGenerateColumns="False" >
            <DataGrid.Columns>
                <DataGridTextColumn Header="Öğrenci Adı" 
                                    Binding="{Binding Ad}"/>
                <DataGridTextColumn Header="Öğrenci Soyadı" 
                                    Binding="{Binding Soyad}"/>
                <DataGridTextColumn Header="1. Yazılı" 
                                    Binding="{Binding Yazili1}"/>
                <DataGridTextColumn Header="2. Yazılı" 
                                    Binding="{Binding Yazili2}"/>
                <DataGridTextColumn Header="Ortalama" 
                                    Binding="{Binding Ortalama}"/>
                <DataGridTextColumn Header="Durum" 
                                    Binding="{Binding Durum}"/>
            </DataGrid.Columns>
        </DataGrid>

    </Grid>
    
```
      


</td>
<td>

![image](https://user-images.githubusercontent.com/28144917/158172593-6c9eb2ec-2820-4fe9-ba96-f4fbe5db06d4.png)    
    
</td>
</tr>
  
  
</table>
    
## DataGrid Özellikleri ##
    
    
<table>
<tr>
<th>
Arayüz Kodları
</th>
<th>
Kullanıcı Arayüzü
</th>
</tr>
<tr>
<td>

```xaml
    
     <DataGrid x:Name="dataGrid1" AutoGenerateColumns="True" 
                  Background="LightGray" 
                  RowBackground="LightYellow" 
                  AlternatingRowBackground="LightBlue"
                  BorderBrush="Purple" BorderThickness="5" 
                  >
            
        </DataGrid>
    
```
      


</td>

<td>

![image](https://user-images.githubusercontent.com/28144917/158173867-c1b78d2a-a0e9-495b-b7fd-3c8ec059fd33.png)    
    
</td>
</tr>
  
  
</table>

    
 ### DataGrid Diğer özellikler ###

    1. IsReadOnly: Sadece okunabilir sutunlar oluşturubailmek için bu özellik kullanılır. 
    2. CanUserSortColumns: Kullanıcının sütün başlıklarına dokunarak sıralama yapabilmesine olanak sağlar
    3. HorizantalScrollBarVisibility: Yatay kaydırma çubuğunu görüntülemek için kullanılır 
    4. VerticalScrollBarVisibility: Dikey kaydırma çubuğunu görüntülemek için kullanılır 
    
    
    <table>
<tr>
<th>
Arayüz Kodları
</th>
<th>
Kullanıcı Arayüzü
</th>
</tr>
<tr>
<td>

```xaml
    
      <DataGrid x:Name="dataGrid1" AutoGenerateColumns="True" 
                  CanUserSortColumns="True"
                  HorizontalScrollBarVisibility="Disabled"
                  
                  >
            
        </DataGrid>
```
      


</td>

<td>

![image](https://user-images.githubusercontent.com/28144917/158175676-39283d05-504d-4036-96dd-70a7bc1cd799.png)   
    
</td>
</tr>
  
  
</table>
