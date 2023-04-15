# MudBlazorVerticalStretchDemo
Demo of vertically stretch content with MudBlazor.

# Required changes to make it work

## 1. Styles

Added wwwroot/css/site.css file
Add site.css to _Layout.cshtml

	<link href="css/site.css" rel="stylesheet" />

- Style for html element:

	Set height to 100%
- Style for body element:

	Set height to 100%

- Reusable stlye .h-100:

	Set elements height to 100%

## 2. MainLayout.razor

- Set MudLayout to 100% height:

		<MudLayout Class="h-100">

- Set MusMainContent to 100% height:

		<MudMainContent Class="h-100">

- Unrelated changes

	* Added a footer ((ab-)using the MudAppBar control wuth a custom height

	* Setting the height of the footer as bottom padding to the MudMainContent

	* Changes to valigation

## 3. FetchData.razor

- Outer MudContainer (moved from MainLayout)

		<MudContainer MaxWidth="MaxWidth.ExtraExtraLarge" Class="h-100 d-flex flex-column">

	* Stretch horizontally

		Set MaxWidth to MaxWidth.ExtraExtraLarge

	* Stretch vertically:
	
		Set height to 100%

	* Make it a flex column

- Replace table with MudDataGrid and make it fill the remaining content

		<MudDataGrid Items="forecasts" Virtualize="true" FixedHeader="true" Height="100%" Class="h-100 flex-grow-1 overflow-hidden">
			<Columns>
				<PropertyColumn Property="x => x.Date" />
				<PropertyColumn Property="x => x.TemperatureC" Title="°C" />
				<PropertyColumn Property="x => x.TemperatureF" Title="°F" />
				<PropertyColumn Property="x => x.Summary" />
			</Columns>
		</MudDataGrid>

	* FixedHeader=true
		
		to only scroll the rows

	* Height=100% 
		
		to strecth the inner content of the data grid

	* Class="h-100 flex-grow-1 overflow-hidden"

		to make it fill the remaining content of the flex column without overflowing

	* Also increased the number of rows from 5 to 50 in the forecast data model