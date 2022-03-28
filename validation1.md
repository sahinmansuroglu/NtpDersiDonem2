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
### Int32.TryParse() ile sayısal değer kontrolü ##

**Örnek**
> Aşağıdaki örnekte txtDogumYili adlı text kutusunun içeriği tamsayıya çevrilmeye çalışılır. Eğer çevrim başarılı ise "true" değeri döner başarısız ise "false" değeri döner. Ayrıca çevrim başarılı olduğunda gecerliDogumYili değişkenine doğum yılının int tipindeki değeri atanır. Çevrim gerçekleşmezse int tipinin varsayılan değeri olan 0 değeri atanır.

```csharp
 bool dogumTarihiSayisalmi = Int32.TryParse(txtDogumYili.Text, out int gecerliDogumYili);

                    if (dogumTarihiSayisalmi == false)
                    {
                        MessageBox.Show("Doğum Tarihi girilmeli ve Rakam olmalı");

                    }
```

### Veri Doğrulama Örneği ###


![image](https://user-images.githubusercontent.com/28144917/160339486-b35fd2f9-6a10-4479-ae50-b547234332ae.png)

> Yukarıda kullanıcı arayüzü verilen uygulamada aşağıda belirtilen doğrulamalar yapıldıktan sonra Ad Soyad, Dogum Yılı ve Puanı bir metin içerisinde birleştirilerek listbox'a ekletilmiştir.
<ol>
            <li>Öğrenci Ad Soyadı Boş Geçilirse "Lütfen Ad Soyad Giriniz" uyarısı verilecek</li>
<li>Öğrenci Ad Soyadı 6 Karakterden az ise ""Ad Soyad en az 6 karakterden olusmali"" uyarısı verilecek</li>
<li>Doğum Yılı boş geçilirse veya rakam dışında bir karakter girilirse "Doğum Tarihi girilmeli ve Rakam olmalı" uyarısı verilecek</li>
<li>Doğum Yılı 1910'dan Küçükse "Dogum yili 1910'dan Küçük olamaz" uyarısı verilecek</li>
<li>Doğum Yılı Güncel yıldan büyükse "Doğum yılı Bulunulan Yıldan Fazla olamaz" uyarısı verilecek</li>
<li>Puan boş geçilirse veya rakam dışında bir karakter girilirse "Puan girilmeli ve Rakam olmalı" uyarısı verilecek</li>
<li>Puan 0-100 arası değilse "Puan 0-100 arası olmalı" uyarısı verilecek</li>

            
**Çözüm (Butona tıklandığında yapılan kontroller)**
            
```csharp
private void Button_Click(object sender, RoutedEventArgs e)
        {
            bool adSoyadGirisiDogrumu = string.IsNullOrEmpty(txtAdSoyad.Text.Trim());
            if (adSoyadGirisiDogrumu == true)
            {
                MessageBox.Show("Lütfen Ad Soyad Giriniz");

            }
            else
            {
                int karakterSayisi = txtAdSoyad.Text.Trim().Length;

                if (karakterSayisi < 6)
                {
                    MessageBox.Show("Ad Soyad en az 6 karakterden olusmali");
                }
                else
                {

                    bool dogumTarihiSayisalmi = Int32.TryParse(txtDogumYili.Text, out int DogumYili);

                    if (dogumTarihiSayisalmi == false)
                    {
                        MessageBox.Show("Doğum Tarihi girilmeli ve Rakam olmalı");

                    }
                    else
                    {
                        if (DogumYili<1910)
                        {
                            MessageBox.Show("Dogum yili 1910'dan Küçük olamaz");
                        }
                        else
                        {
                            if (DogumYili > DateTime.Now.Year)
                            {
                                MessageBox.Show("Doğum tarihi Bulunulan Yıldan Fazla olamaz");
                            }
                            else
                            {

                                bool puanSayisalmi = Int32.TryParse(txtPuan.Text, out int Puan);

                                if (puanSayisalmi == false)
                                {
                                    MessageBox.Show("Puan girilmeli ve Rakam olmalı");
                                    txtPuan.Clear();
                                    txtPuan.Focus();

                                }
                                else
                                {
                                    if (Puan>100 || Puan < 0)
                                    {
                                        MessageBox.Show("Puan 0-100 arası olmalı");
                                    }
                                    else
                                    {

                                        liste1.Items.Add($"{txtAdSoyad.Text} {txtDogumYili.Text} {txtPuan.Text}");
                                        txtPuan.Clear();
                                        txtDogumYili.Clear();
                                        txtAdSoyad.Clear();
                                        MessageBox.Show("Herşey başarılı");
                                    }

                                }


                            }

                        }


                    }

            

                }


            }
```
