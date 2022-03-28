## Veri Doğrulama ## 

### string.IsNullOrEmpty ile veri Doğrulama ##

> Bir String bir değişkeninin içinin boş veya null olup olmadığını test eder. Eğer içeriği boş veya null ise "True" değeri döndürür aksi durumda "False" Döndürür.

**Örnek**
> Aşağıdaki örnekte txtAdSoyad adlı text kutusu karakter girilmeden boş geçilirse true değeri döndürür

```csharp
bool adSoyadGirisiDogrumu = string.IsNullOrEmpty(txtAdSoyad.Text.Trim());
if (adSoyadGirisiDogrumu ==  true)
            {
                MessageBox.Show("Lütfen Ad Soyad Giriniz");

            }
```


### String değişkenlerin Length özelliği ile karakter sayilarının kontrolü ##

**Örnek**
> Aşağıdaki örnekte txtAdSoyad adlı text kutusu 6 karakterden az olursa hata verir.

```csharp
 int karakterSayisi = txtAdSoyad.Text.Trim().Length;

                if (karakterSayisi < 6)
                {
                    MessageBox.Show("Ad Soyad en az 6 karakterden olusmali");
                }
```
