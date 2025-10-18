I asked ChatGPT: "I am working with a polars dataframe in Python. I have latitudes and longitudes of different points and want to map them over the map of Texas, with the size of each point determined by another variable. What packages would work with Polars and Python best to help me do this? Do I need to convert any of the geospatial data beforehand?"

It gave me the following code blocks:

import polars as pl

# Suppose you have a Polars DataFrame
df_polars = pl.DataFrame({
    "lat": [30.2672, 32.7767, 29.4241],
    "lon": [-97.7431, -96.7970, -98.4936],
    "value": [100, 200, 150],
})

# Convert to pandas
df = df_polars.to_pandas()


import geopandas as gpd
from shapely.geometry import Point

# Convert to GeoDataFrame
gdf = gpd.GeoDataFrame(
    df,
    geometry=gpd.points_from_xy(df.lon, df.lat),
    crs="EPSG:4326"  # WGS84 lat/lon
)


texas = gpd.read_file(gpd.datasets.get_path('naturalearth_lowres'))
texas = texas[texas['name'] == 'United States']  # or a shapefile of Texas specifically

texas = gpd.read_file("path/to/texas_shapefile.shp")

ax = texas.plot(color='white', edgecolor='black', figsize=(8,8))
gdf.plot(ax=ax, markersize=gdf['value'], color='red', alpha=0.6)

import folium

m = folium.Map(location=[31, -99], zoom_start=6)

for _, row in df.iterrows():
    folium.CircleMarker(
        location=[row['lat'], row['lon']],
        radius=row['value'] / 50,  # scale your variable
        color='crimson',
        fill=True,
        fill_opacity=0.6
    ).add_to(m)

m.save("texas_map.html")
m

import pydeck as pdk

view_state = pdk.ViewState(latitude=31, longitude=-99, zoom=6)

layer = pdk.Layer(
    "ScatterplotLayer",
    df,
    get_position=["lon", "lat"],
    get_radius="value",
    get_color=[255, 0, 0, 160],
    pickable=True,
)

pdk.Deck(layers=[layer], initial_view_state=view_state)