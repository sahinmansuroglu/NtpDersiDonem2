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
> Aşağıdaki örnekte txtDogumYili adlı text kutusunun içeriği tamsayıya çevrilmeye çalışılır. Eğer çevrim başarılı ise "true" değeri döner başarısız ise "false" değeri döner.

```csharp
 bool dogumTarihiSayisalmi = Int32.TryParse(txtDogumYili.Text, out int gecerliDogumYili);

                    if (dogumTarihiSayisalmi == false)
                    {
                        MessageBox.Show("Doğum Tarihi girilmeli ve Rakam olmalı");

                    }
```

### Veri Doğrulama Örneği ###

![image](https://user-images.githubusercontent.com/28144917/160339486-b35fd2f9-6a10-4479-ae50-b547234332ae.png)


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
