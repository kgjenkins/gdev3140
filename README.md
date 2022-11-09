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

Use themes to control different style configurations for the main and inset
maps.

- In the main QGIS window, make sure all the layers are on.
- Click the eye icon at top of Layers panel
- ...



# Animations

ship data from https://marinecadastre.gov/ais/


