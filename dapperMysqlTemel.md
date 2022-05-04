## Dapper-Mysql ile Veritabanı İşlemleri ##

### Yüklenmesi Gereken Kütüphaneler ###

![image](https://user-images.githubusercontent.com/28144917/156490303-cff9c336-98da-4d58-a953-88e8a69664b4.png)


### Mysql Tablo Yapısı ###

![image](https://user-images.githubusercontent.com/28144917/156490264-64cfc5eb-b6ec-4e5f-a67f-119773b640f5.png)

[Projenin Tamamlanmış Hali İçin Tıklayınız](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8174746/CalisanPRoje.zip)

```csharp 
using System;
using System.Data;
using MySql.Data.MySqlClient;
using Dapper;
using System.Linq;

namespace ConsoleApp1
{
    class Ogr
    {
        public int Id { get; set; }
        public string AdSoyad { get; set; }
        public int OkulNo { get; set; }
        public int Puan1 { get; set; }
        public int Puan2 { get; set; }
        public override string ToString()
        {
            return $"{Id}-{AdSoyad}-{OkulNo}-{Puan1}-{Puan2}";
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
            VeritabaniIslemleri veritabaniIslemleri = new VeritabaniIslemleri();
            veritabaniIslemleri.KayitGuncelle();
            veritabaniIslemleri.tumKayitlariListele();
            Console.ReadKey();
           
        }
    }

    class VeritabaniIslemleri
    {


        string ConnectionString1 = "host=localhost;port=3306;user id=sahin;password=1234;database=eokul;";

        public void tumKayitlariListele()
        {
            using (IDbConnection  connection = new MySqlConnection(ConnectionString1))
            {
                var cars = connection.Query<Ogr>("SELECT * FROM tbl_ogr  ; ").ToList();
                               cars.ForEach(car => Console.WriteLine(car));

            }
        }
        public void yeniKAyitEkle()
        {

            using (IDbConnection  connection = new MySqlConnection(ConnectionString1))
            {

                Ogr yeniOgr = new Ogr
                {
                    AdSoyad = "Mehmet EMİN",
                    OkulNo = 66,
                    Puan1 = 55,
                    Puan2 = 87
                };

                string sqlQuery = "INSERT INTO tbl_ogr (AdSoyad, OkulNo,Puan1,Puan2) VALUES(@AdSoyad, @OkulNo,@Puan1,@Puan2)";
                int rowsAffected = connection.Execute(sqlQuery, yeniOgr);
                Console.WriteLine($"{rowsAffected} kayıt eklendi");

            }
        }

        public void KayitSil()
        {
         
            using (IDbConnection  connection = new MySqlConnection(ConnectionString1))
            {
                string sqlQuery = "DELETE FROM tbl_ogr WHERE Id = @Id;";
                int rowsAffected = connection.Execute(sqlQuery, new { Id = 3 });
                Console.WriteLine($"{rowsAffected} kayıt Silindi");
            }
        }


        public void KayitGuncelle()
        {

            using (IDbConnection  connection = new MySqlConnection(ConnectionString1))
            {
                string sqlQuery = "UPDATE tbl_ogr SET AdSoyad =  @AdSoyad WHERE Id = @Id;";
                int rowsAffected = connection.Execute(sqlQuery, new { Id = 2, AdSoyad = "Şahin MANSUROĞLU" });
                Console.WriteLine($"{rowsAffected} kayıt güncellendi");
            }
        }
        

    }
}

```
**Kaynaklar**

https://riptutorial.com/Download/dapper-net.pdf

https://www.learndapper.com/

https://www.jetbrains.com/dotnet/guide/tutorials/basics/dapper/

https://www.c-sharpcorner.com/UploadFile/e4e3f7/dapper-king-of-micro-orm-C-Sharp-net/

https://github.com/DapperLib/Dapper

https://www.ezzylearning.net/tutorial/crud-operations-in-asp-net-core-5-using-dapper-orm

https://www.borakasmer.com/dapper-nedir/

https://www.geeksforgeeks.org/c-dapper/

https://developerpublish.com/learn-dapper-net-step-by-step-tutorial/
