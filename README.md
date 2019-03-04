_Cribbing fairly heavily from a previous version by Denise Malan and Liz Lucas_

## What is geocoding?

Often we get a dataset with an address for each record, and often we would like to place that address on a map. In order to do that, you need to translate your addresses to latitude/longitude coordinates. The process a computer uses to calculate the coordinates for an address so it can place it on a map is known as geocoding.

### Which one is latitude again?

Latitude = Y axis (north and south)  
Longitude = X axis (east and west) -- Think long and not tall

### OK are we geocoding yet?

No, we are going to talk about boring but important things first.

## How many things do you need to geocode?

1 thing: Google it.  
10 things: Google them.  
100 things: You have so many choices!  
10,000 things: OoooOooooOOOooooo. Meet Geocod.io.*  
Outside North America: Your mileage may vary  

_*Or do it with the Google Geocoding API, if you're going to put it on a Google Map._

## Do you have/need address-level data or city-level data?

Our data: 2,392 California Starbucks locations

## Terms of Service

Always read the terms of service, and don't assume you won't get caught

#### Common restrictions
- Can you cache your lat-lng points?  

- Where are you allowed to use those lat-lng points (often, only in the vendor's own products)

- Cost structure (2,500 free is common, but sometimes that's forever and sometimes that's per day)

## Prepping your data

Ideally, you'll have address, city and state in separate columns.

![Our spreadsheet](img/geocod.io/spreadsheet.png)

And we want the address column with the whole address, not split up (which is better for a mail merge). But if your data only has these separately, it's straightforward to merge them in Excel.

![Our spreadsheet](img/geocod.io/spreadsheet_with_highlighted_cols.png)

# Geocod.io

![Our spreadsheet](img/geocod.io/geocod.io_home.png)

## Creating an account

![Our spreadsheet](img/geocod.io/geocod.io_create_account.png)

## Spreadsheet vs. API

Today we're going to upload as spreadsheet of data, but you can also use Geocod.io's API with bulk data or a single lookup (for example for looking up an address live for a user):

![Our spreadsheet](img/geocod.io/geocod.io_spreadsheet_or_api.png)

## Uploading data

Click on "Drop your spreadsheet here":

![Our spreadsheet](img/geocod.io/geocod.io_upload_spreadsheet.png)

Tell Geocod.io which columns to use:

![Our spreadsheet](img/geocod.io/geocod.io_set_columns.png)

... Then click preview to make sure your addresses landed in sensible places:

![Our spreadsheet](img/geocod.io/geocod.io_preview.png)

... Then click "Yes, looks good."

## Upgrades!

Depending on what you're doing with your data, you might want to append demographic stats for a given address as you geocode. You can do this on your own without Geocod.io, and there is a small cost, but this can save you a lot of time and hassle!

![Appends](img/geocod.io/geocod.io_appends.png)

... But for today, we don't need anything else, just the points. Click "continue."

... And click "Start" to roll the ~~presses~~ geocoder.

## Now we wait

![Now we wait](https://media.giphy.com/media/vdsISoCQMga9G/giphy.gif)

## The hard/important part: Check the results

![Your list of geocoded datasets](img/geocod.io/geocod.io_list.png)

View map for a visual bullshit check...

![Map results](img/geocod.io/geocod.io_map_results.png)

But we need to do better than that and understand what the geocoder did with each address.

![Lion King Look Harder](https://pics.me.me/look-harder-memecrunch-com-29709775.png)

Yes, we have our purported latitude and longitudes. But how accurate are those results? A good geocoder tells you more. We get an numerical score, the method used to place this row, and even the original source of the data used. This allows us to make an educated decision about whether each point (or type of result) is good enough to be used. Note: The numerical score and the method are not the same thing.

![Geocoding results, highlighted](img/geocod.io/geocoding_results_highlighted.png)

#### Common match methods
- rooftop
- nearest_rooftop_match
- range_interpolation

# Example 2: City-level data

Sometimes, often with a national map, it's sufficient to place points in the center of a city. Other times, you might only have city-level precision.

## Rules of the road
- Some cities are very big, so if you're zoomed in close this could be misleading

- Generally the point will map to the CENTROID, or geographic center, of a city, which may or may not be anywhere near the center of activity.

### Los Angeles centroid: in the hills
![Los Angeles](img/geocod.io/los_angeles_centroid.png)

### San Francisco centroid: in the water
![San Francisco](img/geocod.io/san_francisco_centroid.png)

## Find unique cities

## Merge back into your data

# When geocoding goes wrong
