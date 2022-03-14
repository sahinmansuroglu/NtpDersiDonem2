## DataGrid ile veri bağlama ##
> DataGrid verileri tablo halinde gösterebilmek için kullanılan bir kontroldür. Listeleri ve koleksiyonlari tablo halinde görüntülemek isteğimizde DataGrid'ten faydalabiliriz.

Verilen DataGrid Örneklerinde Aşağıdaki Ogrenci sınıfı kullanılacaktır.

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
                  AutoGenerateColumns="False"/>

    </Grid>
```
    
![image](https://user-images.githubusercontent.com/28144917/158160798-e8afdf4f-7401-49f1-ba48-48cfadfc9151.png)


</td>
</tr>
  
  
</table>


