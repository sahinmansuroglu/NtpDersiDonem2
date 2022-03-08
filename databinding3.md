## INotifyPropertyChanged Arayüzünün Kullanımı ##

```csharp

  class Ogrenci: INotifyPropertyChanged
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
                OnPropertyChanged("soyad");
            }
        }
     

        protected internal virtual void OnPropertyChanged(string propertyName)
        {
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
        }

        public event PropertyChangedEventHandler PropertyChanged;
    }
```


Puan Ortalama INotifyPropertyChanged

[WpfApp11.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8209229/WpfApp11.zip)
