## Entity Framework-MYSQL ile Veritabanı İşlemleri ##

**Kurulacak olan Paket**

![image](https://user-images.githubusercontent.com/28144917/164450043-69a313e8-2d24-4d24-a78b-dbee4b7dbd9c.png)



**Örnek Proje**

[DatabaseProject.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8530583/DatabaseProject.zip)



### Ogrenci sınıfı ###
```csharp
 public class Ogrenci
    {
        public int Id { get; set; }
        public string? AdSoyad { get; set; }
        public int yas { get; set; }
    }
    
``` 

### DbContext sınıfı ###
```csharp
using Microsoft.EntityFrameworkCore;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DatabaseProject
{
    public class AppDbContext : DbContext
    {
        protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
        {
            var serverVersion = new MySqlServerVersion(new Version(8, 0, 28));
            optionsBuilder.UseMySql(connectionString: @"server=localhost;userid=root;password=mtal2022;database=eokul", serverVersion);
        }
        public DbSet<Ogrenci>? ogrenci { get; set; }
    }
}

    
``` 


### Ana Program ###
```csharp

using DatabaseProject;

void listele()
{
    using (var db = new AppDbContext())
    {
        var ogrenciler = db.ogrenci.ToList();
        Console.WriteLine("****Öğrenci Listesi****");
        foreach (var ogrenci in ogrenciler)
        {
            Console.WriteLine($"{ogrenci.Id} {ogrenci.AdSoyad} {ogrenci.yas} ");
        }
    }

}
void YeniOgrenciEkle()
{
    
        using (var db = new AppDbContext())
        {
            db.Add(new Ogrenci { AdSoyad = "Ahmet EMİN", yas = 45});
            db.SaveChanges();
        }
    
}


void Ogrencisil(int id)
{
    using (var db = new AppDbContext())
    {
        Ogrenci bulunanOgrenci = db.ogrenci.Find(id);
        if (bulunanOgrenci==null)
        {
            Console.WriteLine("Öğrenci bulunamadı");
            return;
        }

        db.ogrenci.Remove(bulunanOgrenci);
        db.SaveChanges();
    }
}

void OgrenciGuncellel(int id,string yeniAdSoyad, int yeniYas)
{
    using (var db = new AppDbContext())
    {
        Ogrenci bulunanOgrenci = db.ogrenci.Find(id);
        if (bulunanOgrenci == null)
        {
            Console.WriteLine("Öğrenci bulunamadı");
            return;
        }
        bulunanOgrenci.AdSoyad = yeniAdSoyad;   
        bulunanOgrenci.yas = yeniYas;   
        db.SaveChanges();
    }
}

YeniOgrenciEkle();
Ogrencisil(3);
OgrenciGuncellel(4, "Aycan HÜR", 45);
listele();

```
