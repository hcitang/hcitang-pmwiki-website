title: ''
author: ''
appears: ''
updated: Invalid date

---

## ControlTemplates

(:source lang=XML :) <pre class="escaped">

<Window x:Class="WpfApplication1.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Window1" Height="300" Width="300">
    <Window.Resources>
        <Style TargetType="Button" x:Key="EllipseButton">
            <Setter Property="Template">
                <Setter.Value>
                    <ControlTemplate TargetType="Button">
                        <Grid>
                            <Ellipse Fill="{TemplateBinding Background}" Stroke="Black"/>
                            <ContentPresenter HorizontalAlignment="Center"
                                              VerticalAlignment="Center" />
                        </Grid>
                    </ControlTemplate>
                </Setter.Value>
            </Setter>
        </Style>
    </Window.Resources>
    <Grid>
        <Button Height="23" HorizontalAlignment="Left" Margin="34,47,0,0" Name="button1" VerticalAlignment="Top" Width="75">Button</Button>
        <Button Style="{StaticResource EllipseButton}" Margin="34,76,0,0" Name="button2" Height="23" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75">Button</Button>
    </Grid>
</Window>

</pre>
