# Advanced QGIS Styles and Layouts

A workshop for GDEV 3140, 2022-11-09 \
Keith Jenkins, GIS Librarian at Mann Library \
kgj2@cornell.edu


# How to better visualize thousands of points?

2020 automobile crash data derived from
https://fortress.wa.gov/wsp/collisionanalysistool/

- Open the crashes.qgz project

- Adjust marker opacity (in the layer styling panel)
    - set to ~1% when viewing the whole state
    - set higher when zoomed in

- Filter the data to just view a subset
    - right-click the layer name > filter...
    - high-speed roads: "Colli_Unit_Postd_Speed" >= 45

- Point Clusters (combine nearby points into a single marker)
    - in the layer styling panel, change "Single Symbol" to "Point Cluster"
    - set distance to 10 mm
- Dynamic sizing of the cluster markers
    - click the cluster symbol to edit it
    - select the "Simple Marker" part
    - click the "expression" button next to the size setting > edit
    - enter the following expression: sqrt(@cluster_size)
    - look for sharp curve in highway heading east from Seattle

- Point Displacement (offset points so they are all visible)
    - switch back to single symbol, and zoom to south of downtown Seattle
    - in the layer styling panel, change "Single Symbol" to "Point
      Displacement"
    - adjust distance as needed
    - try placement method (ring, concentric rings, grid)

- Heatmap
    - in the layer styling panel, change "Single Symbol" to "Heatmap"
    - edit the color ramp
        - select left stop, set opacity to 0%
        - select right stop, set color to red
    - maximum value "automatic" adjusts well as you change zoom levels
        - but can also adjust via trial and error make light areas more visible

Exercise:
    - change the filter to look at residential roads
        "Colli_Unit_Postd_Speed" <= 35
    - try some of the styles above to see what works best




# Layouts

Tompkins County fire station data derived from
https://tcdata-tompkinscounty.opendata.arcgis.com/datasets/firestations

- Open the layouts.qgz project
- Add labels using the "PLACENAME" field
    - What can be improved about these labels???
    - Hint: Formatting tab
- Open the existing print Layout 1 (Project menu > Layouts)
- Add an inset map in the corner -- to show Tompkins county within NY

We'll use named themes and styles to control different style configurations for the main and inset maps.  First, we'll create a theme for the main map that has the firestations.

- In the main QGIS window, make sure all the layers are on, including the fire stations.
- Click the eye icon at top of Layers panel > Add theme... call it "fire stations"

Now we'll create a theme that omits the fire stations, and just shows the border.

- Uncheck the box to hide the fire station layer
- Click the eye icon > Add theme... call it "border only"

Now we'll configure each map in the layout to use these themes.

- Switch to the layout window
- Select the "Select/Move item" tool to select the main map on the layout
- In the "Item Properties" panel, in the "Layers" section, check the box to "Follow map theme" and select "fire stations"
- Select the inset map, and have it follow map theme "border only"


## Using multiple styles for the same layer

A "theme" in QGIS keeps track of which layers are visible, and which named style is applied to each layer.  Unless you explicitly create a named style for a layer, you are using the "default" style for that layer.  If you wanted to create two different themes, one with red fire station points, and one with blue fire station points, you could create two named styles for the layer:

- In the main QGIS window, right-click the "fire stations" layer name > Styles > Rename current... call it "red points"
- Right-click the layer again > Styles > New Style... call it "blue points"
- Change the color of the points to blue

Now we can create a new theme using the blue points style:

- Click the eye icon > Add theme... call it "blue fire stations"

And to update our layout to use this blue theme:

- In the layout window, set the main map to follow map theme "blue fire stations"


## Changing the CRS of the inset map

Each map item in a QGIS layout can have its own map projection.

- Use the "Select/Move item" tool to select the inset map
- In the Item Properties, set the CRS as desired.
