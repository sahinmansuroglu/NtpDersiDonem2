## Combobox ile String bir listenin bağlanıtısı ##




<table>
<tr>
<th>
Arayüz Kodları
</th>
  <th>
C# kodları 
</th>
  <th>
Kullanıcı Arayüzü
</th>
</tr>
<tr>
<td>

      
```xaml
 <StackPanel Margin="10">
        <ComboBox Name="comboBox1" 
                  Width="100" 
                  SelectedIndex="0"/>
    </StackPanel>
```

</td>
  <td>

      
```csharp
public MainWindow()
        {
            InitializeComponent();
            List<String> sehirler = new List<string>();
            sehirler.Add("Mersin");
            sehirler.Add("Adana");
            sehirler.Add("Ankara");
            comboBox1.ItemsSource = sehirler;
        }
```

</td>
  <td>

![image](https://user-images.githubusercontent.com/28144917/157974892-723d5472-17d4-4fa2-8133-fd6e1a1c7531.png)

</td>
</tr>
  
  <tr>
<td>

      
```xaml

```

</td>
  <td>

      
```xaml

```

</td>
  <td>




</td>
</tr>
</table>

## Combobox ile bir nesne  listenin bağlanıtısı ##

  <table>
<tr>
<th>
Sehir Class'ı
</th>
  <th>
C# kodları 
</th>
  <th>
Kullanıcı Arayüzü
</th>
</tr>
<tr>
<td>

      
```csharp
class Sehir
{
    public int PlakaKodu { 
      get; 
      set;
    }
    public string SehirAdi { 
      get; 
      set;
    }
    public string PlakaVeSehir
    {
       get
        {
         return $"{PlakaKodu}-{SehirAdi}";
        }
    }
}
```

</td>
  <td>

      
```csharp
 public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
            List<Sehir> sehirler = new List<Sehir>();
            sehirler.Add(new Sehir { 
                SehirAdi="Mersin",
                PlakaKodu=33,
            });
            sehirler.Add(new Sehir
            {
                SehirAdi = "İstanbul",
                PlakaKodu = 34,
            });
            sehirler.Add(new Sehir
            {
                SehirAdi = "İzmir",
                PlakaKodu = 35,
            });
         
            comboBox1.ItemsSource = sehirler;
            comboBox1.DisplayMemberPath = "SehirAdi";
        }

    }

  
```

</td>
  <td>

![image](https://user-images.githubusercontent.com/28144917/157976153-bb02d425-16c6-45b6-ac47-21a92e2c0edb.png)

</td>
</tr>
  
 <tr>
<td>

      
```csharp
class Sehir
{
    public int PlakaKodu { 
      get; 
      set;
    }
    public string SehirAdi { 
      get; 
      set;
    }
    public string PlakaVeSehir
    {
       get
        {
         return $"{PlakaKodu}-{SehirAdi}";
        }
    }
}
```

</td>
  <td>

      
```csharp
 public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
            List<Sehir> sehirler = new List<Sehir>();
            sehirler.Add(new Sehir { 
                SehirAdi="Mersin",
                PlakaKodu=33,
            });
            sehirler.Add(new Sehir
            {
                SehirAdi = "İstanbul",
                PlakaKodu = 34,
            });
            sehirler.Add(new Sehir
            {
                SehirAdi = "İzmir",
                PlakaKodu = 35,
            });
         
            comboBox1.ItemsSource = sehirler;
            comboBox1.DisplayMemberPath = "PlakaVeSehir";
        }

    }

  
```

</td>
  <td>

![image](https://user-images.githubusercontent.com/28144917/157976399-f4c050f9-3a4f-4edd-bb96-e8f882b0b1be.png)

</td>
</tr>
</table>
