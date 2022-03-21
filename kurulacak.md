## Kurulacaklar ##

### Programlar ###
      Mysql

### Eklentiler ###
      https://github.com/xceedsoftware/wpftoolkit (ekstra Kontroller için)
      dapper
      mysql.data
      materialUI
  
### İkonlar ###
      https://www.flaticon.com/
      
### Material UI İçin ###


http://materialdesigninxaml.net/ (kurulum ayarları burada)

https://intellitect.com/getting-started-material-design-in-xaml/

https://www.youtube.com/watch?v=-n5yeEOsbCk

[MaterialDesignInXaml.Examples-master.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8311914/MaterialDesignInXaml.Examples-master.zip)

[DemoApp.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8311915/DemoApp.zip)

> wpf tool kit için aşağıdaki gerekli
  
xmlns:xctk="http://schemas.xceed.com/wpf/xaml/toolkit"
      
> Nuget Package

[nugpack.zip](https://github.com/sahinmansuroglu/NtpDersiDonem2/files/8311958/nugpack.zip)

```xaml
<Application . . .>
  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Light.xaml" />
        <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Defaults.xaml" />
        <ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/Recommended/Primary/MaterialDesignColor.DeepPurple.xaml" />
        <ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/Recommended/Accent/MaterialDesignColor.Lime.xaml" />
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>


<Window . . .
     xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
     TextElement.Foreground="{DynamicResource MaterialDesignBody}"
     TextElement.FontWeight="Regular"
     TextElement.FontSize="13"
     TextOptions.TextFormattingMode="Ideal"
     TextOptions.TextRenderingMode="Auto"
     Background="{DynamicResource MaterialDesignPaper}"
     FontFamily="{DynamicResource MaterialDesignFont}">
  <Grid>
    <materialDesign:Card Padding="32" Margin="16">
      <TextBlock Style="{DynamicResource MaterialDesignTitleTextBlock}">My First Material Design App</TextBlock>
    </materialDesign:Card>
  </Grid>
</Window>
```
