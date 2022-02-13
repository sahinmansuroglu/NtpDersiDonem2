## WPF - Dependency Properties ##

 <Button  Height = "40" Width = "175" Margin = "10" Content = "Dependency Property">
            <Button.Style>
                <Style TargetType = "{x:Type Button}">
                    <Style.Triggers>

                        <Trigger Property = "IsMouseOver" Value = "True">
                            <Setter Property = "BorderThickness" Value = "5" />
                            <Setter Property = "Foreground" Value = "red" />
                        </Trigger>

                    </Style.Triggers>
                </Style>
            </Button.Style>
        </Button>
