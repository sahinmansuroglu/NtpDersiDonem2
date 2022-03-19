## MessageBox ##

<table>
<tr>
<th>
C# Kodları
</th>
 
  <th>
Kullanıcı Arayüzü
</th>
</tr>
<tr>

  <td>

      
```csharp
  MessageBox.Show("Merhaba BT Öğrencileri");
```

</td>
  <td>
    
![image](https://user-images.githubusercontent.com/28144917/159108259-419fb412-6b33-4751-8dcd-2696d2ac6017.png)


</td>
</tr>
  
  <tr>

  <td>

      
```csharp
         MessageBox.Show("Merhaba BT Öğrencileri",
                            "KAyıt Uygulaması",
                            MessageBoxButton.OK);
```

</td>
  <td>
   
![image](https://user-images.githubusercontent.com/28144917/159108339-491fcd00-e9fe-4e80-b059-e2b9f287a42f.png)

</td>
</tr>
  
  <tr>

  <td>

      
```csharp
 MessageBox.Show("Merhaba BT Öğrencileri",
                            "Kayıt Uygulaması",
                            MessageBoxButton.OKCancel,
                            MessageBoxImage.Information);
```

</td>
  <td>

![image](https://user-images.githubusercontent.com/28144917/159108381-e5b0c44e-3aec-4cf7-b239-37f06fc514e9.png)

</td>
</tr>
  
  
  
</table>

> MessageBox için kullanılacak Buton Türleri

   1. OK
   2. OKCancel
   3. YesNoCancel
   4. YesNo



> Verilen Cevaba Göre farklı işlemler yapmak için aşağıdaki kodu inceleyebilirsiniz.

```csharp

 MessageBoxResult cevap = MessageBox.Show("Kaydı Silmek İstediğinizden Emin Misiniz",
                            "Kayıt Uygulaması",
                            MessageBoxButton.YesNoCancel,
                            MessageBoxImage.Question);

            switch (cevap)
            {
                case MessageBoxResult.Yes:
                    MessageBox.Show("Kayıt Siliniyor", "Kayıt Uygulaması");
                    break;
                case MessageBoxResult.No:
                    MessageBox.Show("Kayıt Silinmedi", "Kayıt Uygulaması");
                    break;
                case MessageBoxResult.Cancel:
                    MessageBox.Show("İşlem İptal Edildi", "Kayıt Uygulaması");
                    break;
            }
```

![image](https://user-images.githubusercontent.com/28144917/159108641-03a13262-3157-4ad6-84c4-50d7d3948693.png)


> MessageBox için kullanılacak ICON Türleri

    Asterisk
    Error
    Exclamation
    Hand
    Information
    None
    Question
    Stop
    Warning

### Tamamlanmış Uygulama ###

**Arayüz**

![image](https://user-images.githubusercontent.com/28144917/159108934-585b147e-b2e1-4cb3-a6d4-f3bbab06872a.png)


**XAML kodları **


```xaml
 <StackPanel HorizontalAlignment="Center" VerticalAlignment="Center">
        <StackPanel.Resources>
            <Style TargetType="Button">
                <Setter Property="Margin" Value="0,0,0,10" />
                <Setter Property="FontSize" Value="15" />
                <Setter Property="Padding" Value="10" />
            </Style>
        </StackPanel.Resources>
        <Button Name="btnTemelMsgBox" 
                Click="btnTemelMsgBox_Click">Temel MessageBox</Button>
        <Button Name="btnBaslikliMsgBox" 
                Click="btnBaslikliMsgBox_Click">Başlıklı MessageBox </Button>
        <Button Name="btButonluMsgBox" 
                Click="btButonluMsgBox_Click">Butonlu MessageBox </Button>
        <Button Name="btnCevaplıMsgBox" 
                Click="btnCevaplıMsgBox_Click">Cevaplı MessageBox </Button>
        <Button Name="btnIkonluMsgBox" 
                Click="btnIkonluMsgBox_Click">Ikonlu MessageBox </Button>
        <Button Name="btnVarsayilanCevapliMsgBox" 
               Click="btnVarsayilanCevapliMsgBox_Click">Varsayılan Seçimli MessageBox</Button>
    </StackPanel>
```

**C# kodları **


```csharp

 public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }
       
        private void btnTemelMsgBox_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Merhaba BT Öğrencileri");
        }

        private void btnBaslikliMsgBox_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Merhaba BT Öğrencileri",
                            "KAyıt Uygulaması",
                            MessageBoxButton.OK);
        }

        private void btButonluMsgBox_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Merhaba BT Öğrencileri",
                            "Kayıt Uygulaması",
                            MessageBoxButton.OKCancel
                            );
        }

        private void btnCevaplıMsgBox_Click(object sender, RoutedEventArgs e)
        {
            MessageBoxResult cevap = MessageBox.Show("Kaydı Silmek İstediğinizden Emin Misiniz",
                            "Kayıt Uygulaması",
                            MessageBoxButton.YesNoCancel,
                            MessageBoxImage.Question);

            switch (cevap)
            {
                case MessageBoxResult.Yes:
                    MessageBox.Show("Kayıt Siliniyor", "Kayıt Uygulaması");
                    break;
                case MessageBoxResult.No:
                    MessageBox.Show("Kayıt Silinmedi", "Kayıt Uygulaması");
                    break;
                case MessageBoxResult.Cancel:
                    MessageBox.Show("İşlem İptal Edildi", "Kayıt Uygulaması");
                    break;
            }
        }

        private void btnIkonluMsgBox_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Merhaba BT Öğrencileri",
                           "Kayıt Uygulaması",
                           MessageBoxButton.OKCancel,
                           MessageBoxImage.Information);
        }

        private void btnVarsayilanCevapliMsgBox_Click(object sender, RoutedEventArgs e)
        {
            MessageBoxResult cevap = MessageBox.Show("Kaydı Silmek İstediğinizden Emin Misiniz",
                           "Kayıt Uygulaması",
                           MessageBoxButton.YesNoCancel,
                           MessageBoxImage.Question,
                           MessageBoxResult.No);
        }
    }
```
