## Resource Dictionary Kapsamı ##

>Kaynaklar (Resources), kaynak sözlüklerinde (Resource Dictionary) tanımlanır, ancak bir kaynak sözlüğünün tanımlanabileceği çok sayıda yer vardır. 

>Aşağıdaki örnekte, Pencere(Window) düzeyinde bir kaynak sözlüğü (Resource Dictionary) tanımlanmıştır ve bu sözlük içerisinde bir style tanımlanmıştır. Bu stil Pencere düzeyindeki bir sözlükde tanımlandığı için  sadece tanımlandığı pencere  içerisinde kullanılır. 

```xaml
<Window x:Class="WpfApp26.MainWindow"
        ........>

    <Window.Resources>
        
        <Style TargetType="Label" x:Key="labelStil">
            <Setter Property="Background" Value="LightPink"/>
            <Setter Property="Foreground" Value="DarkBlue"/>
            <Setter Property="BorderThickness" Value="5"/>
            <Setter Property="BorderBrush" Value="Purple"/>
        </Style>

    </Window.Resources>
    
    
    <Grid>
        <Label Content="Merhaba Dünya"  Style="{StaticResource labelStil}" />
        <Label Content="Metin 1"  Style="{StaticResource labelStil1}" />
    </Grid>
</Window>

```

### Kapsam Türleri ###
>Kapsam Türleri temel olarak aşağıdaki gibidir

  1. Uygulama Kapsamı (Application Level)
  2. Pencere/Sayfa Kapsamı (Window/Page Level)
  3. Element Kapsamı (Grid, StackPanel Gibi)

#### 1. Uygulama Kapsamı (Application Level) ####
>Aşağıdaki gibi App.xaml içerisinde tanımlanan kaynaklar tüm uygulama içerisinde kullanılır.

![image](https://user-images.githubusercontent.com/28144917/156135310-bfbe3545-a60b-4e3a-8856-bea6689eabe8.png)

#### 2. Pencere/Sayfa Kapsamı (Window/Page Level) ####
>Aşağıdaki gibi Window içerisinde tanımlanan kaynaklar sadece tanımlandığı Window içerisinde kullanılır.

![image](https://user-images.githubusercontent.com/28144917/156135612-80a71f09-4c91-4eb8-ac36-25a51c22403e.png)

#### 3. Element Kapsamı (Grid, StackPanel Gibi) ####

>Aşağıdaki gibi Grid  içerisinde tanımlanan kaynaklar sadece tanımlandığı Grid içerisinde kullanılır.

 ![image](https://user-images.githubusercontent.com/28144917/156136083-8956e675-4cb3-4cf8-b5a8-91b453378f5d.png)

>Aşağıdaki örnekte de StackPanel  içerisinde tanımlanan kaynaklar sadece tanımlandığı StackPanel içerisinde kullanılır.

![image](https://user-images.githubusercontent.com/28144917/156136428-c75e681c-5d64-46cf-bd34-c97c621a1bc3.png)


### Harici Kaynak Sözlüğü oluşturmak ###
> Harici kaynak Sözlüğü oluşturmak için aşağıdaki şekilde uygulamaya sözlük eklenebilir

![image](https://user-images.githubusercontent.com/28144917/156136860-1e0cab08-2b29-42e2-93dc-c5b55a8a553b.png)

> Ardından Aşağıdaki gibi istenilen kaynaklar sözlüğe eklenir

![image](https://user-images.githubusercontent.com/28144917/156137123-c5176844-7754-4ee4-a31c-abc77833f8ff.png)

### Harici Kaynak Sözlüğü Kullanmak ###

> Oluşturulan harici kaynak sözlüğünü kullanabilmek için kaynak sözlüğünün kullanılacağı yerde aşağıdaki çağrılması gerekir.

```xaml
 <(App/Window/Grid).Resources>
        <ResourceDictionary>
                    <ResourceDictionary.MergedDictionaries>
                        <ResourceDictionary Source="Dictionary1.xaml"/>
                    </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
  </(App/Window/Grid).Resources>
```

