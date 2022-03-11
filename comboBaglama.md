## Combobox ile String bir listenin bağlanıtısı ##


| Arayüz Kodları |C# kodları |Kullanıcı Arayüzü|
|:--------:|:----------------------------:|:----------------------------:|
||||
||||
||||
||||

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
