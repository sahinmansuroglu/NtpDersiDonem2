### Kullanılacak olan Class'lar ### 

```csharp
public class Ders
    {
        public int Id { get; set; }
        public string DersKodu { get; set; }
        public string DersAdi { get; set; }
        public int DersSaati { get; set; }
        public  string DersBaslik {
            get
            {
                return $"{DersKodu} : {DersAdi}  )";
            }

        }
    }
  public class Ogrenci
    {
        public int Id { get; set; }
        public string Ad { get; set; }
        public int? OkulNo { get; set; }
        public string Soyad { get; set; }
        public override string ToString()
        {
            return $"{OkulNo} : {Ad} {Soyad} ";
        }
    }
   public class OgrenciPuan
    {
        public int Id { get; set; }
        public int OgrenciId { get; set; }
        public int DersId { get; set; }
        public int? Yazili1 { get; set; }
        public int? Yazili2 { get; set; }
        public int? Performans1 { get; set; }
        public int? Performans2 { get; set; }
        public double? Ortalama { get; set; }
        public string Durum { get; set; }

        public void OrtalamaVeDurumHesapla()
        {
            Ortalama = (Yazili1 + Yazili2 + Performans1 + Performans2) / 4.0;
            Durum = Ortalama < 50 ? "Kaldı" : "Geçti";
        }
       

    }
    
     public class OgrenciPuanModel : OgrenciPuan
    {


        public String DersAdi { get; set; }
        public int DersSaati { get; set; }
        public int OkulNo { get; set; }
        public String Ad { get; set; }
        public String Soyad { get; set; }


        public override string ToString()
        {
            return $"{Ad} {DersAdi} {Performans1}";

        }

        public string AdSoyad { 
            get { 
                return $"{Ad} {Soyad}"; 
            } 
        }

    }
    
```

Tablonun SQL Kodları

[sinavVeritababaniKodlari.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8778955/sinavVeritababaniKodlari.zip)





### Tabloları Birleştirme ###

```sql
select ders.DersAdi, ogrencipuan.Performans1,ogrenci.Ad
from ogrencipuan
inner  join ders
on ders.DersKodu=ogrencipuan.DersKodu
inner  join ogrenci
on ogrenci.Id=ogrencipuan.OgrenciId
```


```sql
select ders.*, ogrencipuan.*,ogrenci.* from ogrencipuan  
inner  join ders on ders.DersKodu = ogrencipuan.DersKodu 
inner join ogrenci on ogrenci.Id = ogrencipuan.OgrenciId
                               
```

### Ders İşlemlerinin Boş bir  projede adım adım yapıldığı dökmanı aşağıdan İndirebilirsiniz. ###
[EOKULPROJE.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8778989/EOKUPROJE.zip)

### Proje Dosyası ###

[VeritabaniProjesi Tamamlanmış.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8778960/VeritabaniProjesi.Tamamlanmis.zip)

[Kütüphaneler Eklenmiş Boş Proje Dosyasını indirmek için tıklayınız.](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8708203/VeritabaniProjesiBos.zip)
