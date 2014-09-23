MainPage.xaml:


<phone:PhoneApplicationPage
    x:Class="PageCaptureExample.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:phone="clr-namespace:Microsoft.Phone.Controls;assembly=Microsoft.Phone"
    xmlns:shell="clr-namespace:Microsoft.Phone.Shell;assembly=Microsoft.Phone"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d" d:DesignWidth="480" d:DesignHeight="768"
    FontFamily="{StaticResource PhoneFontFamilyNormal}"
    FontSize="{StaticResource PhoneFontSizeNormal}"
    Foreground="{StaticResource PhoneForegroundBrush}"
    SupportedOrientations="Portrait" Orientation="Portrait"
    shell:SystemTray.IsVisible="True">
 
    <!--LayoutRoot is the root grid where all page content is placed-->
    <Grid x:Name="LayoutRoot" Background="Transparent">
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
 
        <!--TitlePanel contains the name of the application and page title-->
        <StackPanel x:Name="TitlePanel" Grid.Row="0" Margin="12,17,0,28">
            <TextBlock x:Name="ApplicationTitle" Text="PageCaptureExample" Style="{StaticResource PhoneTextNormalStyle}"/>
            <TextBlock x:Name="PageTitle" Text="main page" Margin="9,-7,0,0" Style="{StaticResource PhoneTextTitle1Style}"/>
        </StackPanel>
 
        <Grid x:Name="ContentPanel" Grid.Row="1" Margin="12,0,12,0"
              Background="{StaticResource PhoneAccentBrush}">
 
            <TextBlock Text="Tap anywhere to capture page"
                       HorizontalAlignment="Center"
                       VerticalAlignment="Center" />
 
            <Image Name="img"
                   Stretch="Fill" />
        </Grid>
    </Grid>
</phone:PhoneApplicationPage>

MainPage.xaml.cs 

using System;
using System.Windows;
using System.Windows.Input;
using System.Windows.Media.Imaging;
using Microsoft.Phone.Controls;
 
namespace PageCaptureExample
{
    public partial class MainPage : PhoneApplicationPage
    {
        // Constructor
        public MainPage()
        {
            InitializeComponent();
        }
        protected override void OnManipulationStarted(ManipulationStartedEventArgs args)
        {
            img.Source = new WriteableBitmap(this, null);
 
            args.Complete();
            args.Handled = true;
            base.OnManipulationStarted(args);
        }
    }
}
