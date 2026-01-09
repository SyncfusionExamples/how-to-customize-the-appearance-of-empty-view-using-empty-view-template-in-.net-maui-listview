# how-to-customize-the-appearance-of-empty-view-using-empty-view-template-in-.net-maui-listview

This demo shows about how to customize the appearance of empty view using EmptyViewTemplate in .NET MAUI ListView

## XAML 
<Grid Margin="0">
    <Grid.RowDefinitions>
        <RowDefinition Height="30"/>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="30"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>
    <Label Grid.Row="0" Text="Inventory Management" TextColor="#E3000000" FontFamily="Roboto-Medium" CharacterSpacing="0.25" FontSize="16" Margin="8,10,0,0" />

    <Grid  x:Name="headerGrid" Grid.Row="1" Margin="8,16,8,16">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>

        <SearchBar x:Name="filterText"                                
                        Grid.Column="0"                              
                        FontSize="16"
                        IsVisible="true"                           
                        TextColor="Gray"
                        Placeholder="Filter Inventory" VerticalTextAlignment="Center" Margin="0,0,8,0">
        </SearchBar>

        <Grid Grid.Column="1" x:Name="sortImageParent">
            <Label HeightRequest="40" VerticalOptions="Center" VerticalTextAlignment="Center" HorizontalOptions="End"
                    FontSize="{OnPlatform MacCatalyst=30, Android=30, iOS=30, UWP=Large}"
                    TextColor="Gray"
                    FontFamily="{OnPlatform iOS=ListViewFontIcons, MacCatalyst=ListViewFontIcons, Android=ListViewFontIcons.ttf#, UWP=ListViewFontIcons.ttf#ListViewFontIcons}"
                    Text="{Binding Path=SortingOptions, Converter={StaticResource BoolToSortIconConverter}}"/>
        </Grid>
    </Grid>
    <Grid Grid.Row="2" Margin="8,0,8,0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto"/>
            <ColumnDefinition Width="*"/>
        </Grid.ColumnDefinitions>
        <Label HorizontalOptions="Start" FontFamily="Roboto-Medium" TextColor="#666666"  Grid.Column="0" Text="Stocks" FontSize="14" CharacterSpacing="0.15"/>
        <Label HorizontalOptions="End" FontFamily="Roboto-Medium" TextColor="#666666" Grid.Column="1" Text="Quantity" FontSize="14" CharacterSpacing="0.15"/>
    </Grid>

    <syncfusion:SfListView x:Name="listView" 
                Grid.Row="3"
                SelectionMode="None"                                     
                ItemsSource="{Binding Items}"                      
                ItemSize="56">

        <syncfusion:SfListView.EmptyView>
            <local:FilterItem Filter="{Binding Source={x:Reference filterText},Path=Text}"/>
        </syncfusion:SfListView.EmptyView>

        <syncfusion:SfListView.EmptyViewTemplate>
            <DataTemplate>
                <Label Text="{Binding Filter,StringFormat='{0} is not found'}" HorizontalTextAlignment="Center" VerticalOptions="CenterAndExpand"
                        FontSize="18" FontFamily="Roboto-Regular" TextColor="#666666" Margin="16,0,16,0"/>
            </DataTemplate>
        </syncfusion:SfListView.EmptyViewTemplate>

        <syncfusion:SfListView.ItemTemplate>
            ---
        </syncfusion:SfListView.ItemTemplate>
    </syncfusion:SfListView>
</Grid>

## Requirements to run the demo

* [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) or [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)
* Xamarin add-ons for Visual Studio (available via the Visual Studio installer).

## Troubleshooting

### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.
