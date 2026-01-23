**Land Stability**

Description:

The land stability algorithm uses Interferometric SAR (InSAR) techniques to determine whether the stability of peat bogland is suitable for windfarm development.

The InSAR technique uses Sentinel-1’s Single Look Complex (SLC) product. Millimetre-sized changes can be tracked using InSAR by studying the same area at two different time points. This means that changes that cannot be seen by the human eye can be tracked. Areas exhibiting larger changes over time are deemed to be at higher risk of instability.

The Intermittent Small Baseline Subset (SBAS) InSAR technique is used to derive displacement and velocity. This technique uses short temporal and spatial gaps or “baselines” between interferometric image pairs to reduce the effects of decorrelation.

Agency: TechWorks Marine

Sensor: Algorithm

**Wind Turbine Wake Effect**

Description:

The turbulence that occurs downfield to a windfarm (the wake) can be observed by Sentinel-1. The consequence of this more turbulent air can be a reduction in wind resource in other windfarms downfield. Depending on the prevailing wind direction, newly constructed offshore wind farms can “steal” the wind resource from existing wind farms.

The capability’s purpose is to show the wind and current direction from CMEMS model data overlayed on Sentinel-1 IW GRD SAR data and is intended to be visualised in areas with offshore wind farms. Under certain conditions, the SAR data can show that upstream turbines have an effect on the wind reaching downstream turbines. The model data is used to verify that the visible effect seen in the images is in fact wind related and not current related.

Agency: TechWorks

Sensor: Algorithm

**Normalised Difference Turbidity Index**

Description:

Offshore wind farms require power cables to be connected to a grid point onshore. These power cables are buried in the seabed:

-   To prevent cable damage from storms and in-water activities occurring above the cables.
-   To minimise wear to the cables.
-   To minimise disruption to plant and animal life on the seabed (post-burial).

The dynamic coastal environment can expose offshore wind farm cabling and is a leading cause in the disruption of operations for offshore wind farms. By studying this dynamic environment using EO data, coupled with physical coastal erosion events, planning for cable onshoring activities can be undertaken in far greater detail by the industry.

Agency: TechWorks Marine

Sensor: Algorithm

**Harshness Index**

Description:

The Harshness Index generates harshness maps based on wave height, sea ice concentration, and iceberg density data. The user can set the magnitude of each variable that is considered 'harsh' and the weight that is given the variable.

A harshness/attractiveness index is a single parameter which combines various data to provide an overall measure of the environmental harshness or attractiveness of a region. In general, the index is given by the following formula:

![](media/584bbe33bd1e657db51c6baf727826f1.emf)

Where:

-   Vi is the ith variable
-   Wi is the weight assigned to the nth variable. ![](media/a9b4f8c26d3b1e1110caff19d1cf7788.emf)
-   Ni is the normalization factor for the ith variable – typically the largest expected value of Vi.

The default harshness index used in the CIF is the Fleming-Drover Harshness Index which takes into account:

-   Mean annual number of days with a sea ice concentration greater than six-tenths (C)
-   Mean annual number of days with a significant wave height greater than four meters (W)
-   Mean annual open-water iceberg areal density (D)

Values for these parameters are normalized before incorporating them into the Harshness Index calculation. In the cases of pack ice and waves, the numbers of days exceeding the criteria were divided by 350 and 110, respectively. These values represent the approximate maximum values expected. For iceberg density, the values were normalized (on scale of 0 to 10) by calculating the logarithm of the iceberg density as follows:

-   For iceberg density of -6 (log of 10-6 km-2) or lower, a value of 0
-   For iceberg density of -1 (log of 10-1 km-2), a value of 10
-   Otherwise, a linear scaling between 0 and 10

The Fleming-Drover Harshness Index is given by the formula when:

-   V1 is the average number of days per year with a sea ice concentration \> 60%
-   V2 is the average number of days per year with a significant wave height \> 4 metres
-   V3 is the average annual iceberg density (number of icebergs per 100 km2)
-   W1 is 6
-   W2 is 2.5
-   W3 is 1.5
-   N1 is 350
-   N2 is 110
-   N3 is (12 + 2\*log10(V3))
-   The iceberg density is within the given range

The harshness/attractiveness index can be customized to use other variables and equations.

Agency: C-CORE

Sensor: Algorithm

**Structure Icing Index**

Description:

The structure icing index is a single parameter which considers sea surface temperature, wind speed, air temperature, and sea ice concentration data to provide a prediction of structure icing rates in different ocean regions.

The Icing Predictor Index is calculated using the following formula: [Va \* (Tf-Ta)] / [1 + 0.3\*(Tw-Tf)], where parameters are:

-   Va - wind speed (ms-1)
-   Tf - seawater freezing temperature (°C)
-   Ta - ambient air temperature (°C)
-   Tw - sea surface temperature (°C)

Icing Predictor values are categorized into the following levels:

-   PR less than or equal to 0 - no icing
-   PR between 0 and 22 - light icing (icing rate \< 0.7 cm/hour)
-   PR between 22 and 53 - moderate icing (icing rate between 0.7-2.0 cm/hour)
-   PR between 53 and 83 - heavy icing (icing rate between 2.0-4.0 cm/hour)
-   PR greater than 83 - extreme icing (icing rate \> 4.0 cm/hour)

Agency: C-CORE

Sensor: Algorithm

**Sea Ice Motion Animation**

Description:

There can be a long wait for the next satellite image to be received during which sea ice can move a considerable distance. The Sea Ice Motion Animation algorithm transforms a satellite image using a sea ice drift forecast to simulate what the ice in a region should look like in the future. The algorithm uses the neXtSIM model for ice drift forecasts up to six hours ahead.

The neXtSIM model is a lagrangian sea ice model designed to address the challenges posed by the highly non-linear and evolving dynamics of Arctic sea ice. It employs an elasto-brittle rheology to capture the fracturing and deformation of sea ice with high fidelity. The model is forced with atmospheric and oceanic inputs from ECMWF and TOPAZ5 respectively and provides detailed forecasts of variables such as ice concentration, thickness, and most importantly, the sea ice drift in u and v components, which is used in the sea ice motion animation.

The following parameters are defined by the user:

-   forecast duration: Number of hours the forecast should run, starting at the timestamp of the input image file,
-   GCP separation: The maximum distance in pixels between the ground control points automatically set throughout the image.

By default, ground control points (GCPs) are set in the four corners of the image. However, the number of GCPs can be increased, placing more points across the image and hence increasing the resolution of the following image warping. The procedure uses an hourly time step, until the forecast reaches the end of the forecast time window. The transformation of the image is performed by the Thin Plate Spline (TPS) algorithm, which is a mathematical model used for non-rigid image alignment and deformation, offering a smooth mapping between points in two-dimensional space. It operates by minimizing the bending energy of a smooth surface that passes through a set of control points, making it ideal for warping applications.

Agency: Drift+Noise

Sensor: Algorithm

**Ship Risk Analysis (POLARIS)**

Description:

POLARIS uses Risk Index Values (RIVs) which are assigned to a ship based on the ice class. The RIVs may be used to evaluate the limitations of the ship operating in an ice regime using input either from historic or current ice charts for voyage planning or in real time from the bridge of the ship.

RIVs are assigned to the ship based on ice class and ice types present according to lookup tables. For each ice regime encountered, the Risk Index Values are used to determine a Risk Index Outcome (RIO) that forms the basis of the decision to operate or the limitation of operations.

The RIO is determined by a summation of the RIVs for each ice type present in the ice regime multiplied by its concentration (expressed in tenths):

RIO = (C1xRIV1) + (C2 x RIV2) + (C3 x RIV3) + … (Cn x RIVn)

Where:

-   C1…Cn are the concentrations (in tenths) of ice types within the ice regime; and
-   RIV1…RIVn are the corresponding Risk Index Values for each ice type.

POLARIS addresses three levels of operation: normal operation, elevated operational risk and operation subject to special consideration. The RIO values in the following table show these three levels of operation.

RIO Interpretation

| **RIOSHIP**    | **Ice classes PC1-PC7**                    | **Ice classes below PC 7 and ships not assigned an ice class** |
|----------------|--------------------------------------------|----------------------------------------------------------------|
| RIO ≥ 0        | Normal operation                           | Normal operation                                               |
| -10 ≤ RIO \< 0 | Elevated operational risk                  | Operation subject to special consideration                     |
| RIO \< -10     | Operation subject to special consideration | Operation subject to special consideration                     |

Agency: IMO

Sensor: Algorithm

**Sea Ice Drift and Deformation**

Description:

**Sea Ice Drift**

The Nansat sea ice drift algorithm’s initial step is based on feature tracking (FT) but includes an additional pattern matching (PM) step that generates vectors over a regular grid.

1.  Feature Tracking (FT) – in this step, features are extracted from each image in the pair, using the OpenCV ORB algorithm. Features are then matched between the two images where possible to measure the motion of the ice over the time period spanned by the images. Matching features are connected by vectors representing the ice drift, and this forms the output of the FT step.
2.  Pattern Matching (PM) – in this step, the FT output is used as a “first guess” and interpolated/extrapolated as necessary to cover the entire overlapping area between the two images in the pair. A regular grid of latitude/longitude coordinates is defined on the overlapping region, and the first guess from FT is used as a starting point for matching a template from the first image to the best pattern match in the vicinity of the first guess on the second image. This allows for calculation of ice motion across the entire overlap region, filling in the spaces between and around the FT vectors where no matching features were found.

**Sea Ice Deformation**

The gridded ice tracking vectors are used to estimate sea ice deformation. Using the Nansat Ice Tracking algorithm (described above), ice motion vectors are defined for every grid point. The next step is to create a mesh of quadrilaterals based on the ice motion at each grid point. Initially the quadrilaterals are rectangular, however due to the ice motion and corresponding deformation, each of the four vertices will be displaced at the time of the second image. The deformation mesh corresponds to the displaced grid points, producing a variety of quadrilateral shapes resulting from the ice motion. This may be interpreted as a Lagrangian description of the sea ice deformation. The deformation is calculated for each polygon constituting the deformed mesh. The deformation values are calculated for each quadrilateral according to the equations given for divergence, shear, and total deformation.

Agency: C-CORE

Sensor: Algorithm

**Ship Risk Index (AIRSS)**

Description:

The Canadian Arctic Ice Regime Shipping System (AIRSS) is intended to minimize the risk of pollution in Arctic waters due to damage of vessels by ice; to emphasize the responsibility of the shipowner and master for safety; and to provide a flexible framework for decision-making. It applies to Canadian Arctic Class (CAC) and Type (Baltic Class) ships, and requires accurate information for voyage planning, timely ice-charts, and consistent observation of ice conditions.

The AIRSS is a four-step process:

-   First, the user characterizes the ice regime. The ice regime is a region of ice with more or less consistent ice conditions. The ice regime takes into account several important factors of the ice: its concentration, thickness, age, state of decay, and roughness.
-   Second, the vessel Class dependant Ice Multipliers are obtained. Because different vessels have different capabilities in ice-covered waters, each vessel is assessed and assigned to a Vessel Class. This rating reflects the strength, displacement, and power of the vessel. The relative risk damage to a vessel by different types of ice is taken into account using “weighting” factors called Ice Multipliers.
-   Third, the information about the ice regime and the Ice Multipliers are combined to determine the Ice Numeral. (The Ice Numeral is a simple calculation that relates the strength of the ship to the danger presented by different ice regimes.)
-   Fourth, the Ice Numeral is used to decide whether the vessel should proceed or take an alternative route. Ice regimes that are not likely to be hazardous have zero or ‘positive’ Ice Numerals; whereas those regimes that could be dangerous have ‘negative’ Ice Numerals.

Agency: NRC

Sensor: Algorithm

**Route Optimization**

Description:

Agency:

Sensor: Algorithm

**Navigation Protection Program (NPP) Automated Scanning Tool (NAST)**

Description:

Agency: National Research Council of Canada

Sensor: Algorithm

\#\# CIF logo \<!--{as="img" src="https://cif.polarview.org/wp-content/uploads/2024/05/CIF-Logo-v3-125.png" style="width: 40%; height: 200px;"}--\>

\# CIF Use Case: Enhancing Arctic Shipping Decisions with Multi-Layered Earth Observation Data

\#\# Shipping icon \<!--{as="img" src="https://cif.polarview.org/wp-content/uploads/bb-plugin/cache/Shipping-Icon-circle-d3dfaffc3b3ce792813de5d7fdd64fdf-hwxq58bkvn93.png" style="width: 18%; height: 200px;"}--\>

\*\*Sector/Domain:\*\* Arctic Shipping

\*\*Primary Stakeholders:\*\* Commercial shipping operators, scientific missions, tourism vessels, northern logistics planners, marine analysts

\#\# Context and Problem

Ships voyaging through the North Atlantic and Arctic Oceans — where they may encounter sea ice or icebergs — are required under the International Maritime Organization’s \*\*Polar Code\*\* to consult timely and historical ice information to plan the safest possible route.

Traditionally, this means relying on ice charts manually produced by national ice services. While these charts are authoritative, they are time-consuming to create, often low in resolution, and sometimes updated only weekly. Because they generalize conditions over large areas, they can miss critical navigational features like polynyas — narrow cracks in the ice that offer passage. Captains sometimes request raw satellite radar images (SAR) for more immediate and detailed insight, but these are difficult to interpret without training, as ice and rough seas can appear similar.

Navigating safely in the Arctic is high-stakes: a wrong judgment can lead to route delays, excessive fuel use, damage to the vessel, or in severe cases, becoming trapped. What’s needed is a way to bring all this information together — visual, expert, machine-interpreted, and regulatory — into one accessible tool that supports real-time, confident decision-making.

\#\# Four-Layer Arctic Ice Intelligence

The \*\*Cerulean Information Factory (CIF)\*\* addresses this challenge by integrating four key layers of sea ice information into a single decision-support CIF Dashboard. This layered approach enables users to move between high-level assessments and detailed data, depending on their needs and level of expertise.

\#\#\# Raw SAR imagery

Real-time radar images from satellites that offer weather-independent views of current sea ice conditions. These are valuable for visual confirmation but can be difficult to interpret on their own.

\#\# map layer 1 \<!--{as="eox-map" style="width: 100%; height: 500px;" layers='[{"type":"Group","properties":{"id":"OverlayGroup","title":"Overlay Layers"},"layers":[{"type":"Tile","properties":{"id":"overlay_bright;:;EPSG:3857","title":"Overlay labels"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/overlay_base_bright_3857/default/g/{z}/{y}/{x}.png","projection":"EPSG:3857","attributions":"{ Overlay: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors, Made with Natural Earth, Rendering \&copy; \<a href=\\"//eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}}]},{"type":"Group","properties":{"id":"AnalysisGroup","title":"Data Layers"},"layers":[{"type":"Tile","properties":{"id":"sea_floor_depth;:;2017-01-01T00:00:00Z;:;wmts capabilities;:;EPSG:3857","title":"Sea floor depth below geoid"},"source":{"type":"WMTS","url":"https://wmts.marine.copernicus.eu/teroWmts","layer":"GLOBAL_ANALYSISFORECAST_PHY_001_024/cmems_mod_glo_phy_anfc_0.083deg_static_202211--ext--bathy/deptho","style":"default","matrixSet":"EPSG:3857","projection":"EPSG:3857","tileGrid":{"tileSize":[128,128]},"dimensions":{}}}]},{"type":"Group","properties":{"id":"BaseLayersGroup","title":"Base Layers"},"layers":[{"type":"Tile","properties":{"id":"sx-cat_ortho680500;:;EPSG:3857","title":"Terrain Light Stereographic North"},"source":{"type":"TileWMS","url":"//sxcat-demo.eox.at/sxcat_maps/wms","projection":"ORTHO:680500","tileGrid":{"tileSize":[512,512]},"attributions":"{ Terrain light: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }","params":{"LAYERS":"sx-cat_ortho680500","TILED":true}}},{"type":"Tile","properties":{"id":"cloudless-2022;:;EPSG:3857","title":"EOxCloudless 2022"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/s2cloudless-2022_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ EOxCloudless 2022: \<a href=\\"//s2maps.eu\\" target=\\"_blank\\"\>Sentinel-2 cloudless - s2maps.eu\</a\> by \<a href=\\"//eox.at\\" target=\\"_blank\\"\>EOX IT Services GmbH\</a\> (Contains modified Copernicus Sentinel data 2022) }"}},{"type":"Tile","properties":{"id":"terrain-light;:;EPSG:3857","title":"Terrain light"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/terrain-light_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ Terrain light: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}},{"type":"Tile","properties":{"id":"eox-osm;:;EPSG:3857","title":"OSM Background"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/osm_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ OSM: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}}]}]' zoom="4" center=[-35.64662933349613,43.27388039326814] projection="" }--\>

\#\#\# Human-made ice charts

Expert-drawn maps from national ice services that classify ice by type and concentration. These charts remain a legal reference point under the Polar Code, but are labor-intensive and often lack spatial detail.

\#\# map layer 2 \<!--{as="eox-map" style="width: 100%; height: 500px;" layers='[{"type":"Group","properties":{"id":"OverlayGroup","title":"Overlay Layers"},"layers":[{"type":"Tile","properties":{"id":"overlay_bright;:;EPSG:3857","title":"Overlay labels"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/overlay_base_bright_3857/default/g/{z}/{y}/{x}.png","projection":"EPSG:3857","attributions":"{ Overlay: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors, Made with Natural Earth, Rendering \&copy; \<a href=\\"//eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}}]},{"type":"Group","properties":{"id":"AnalysisGroup","title":"Data Layers"},"layers":[{"type":"Tile","properties":{"id":"sea_floor_depth;:;2017-01-01T00:00:00Z;:;wmts capabilities;:;EPSG:3857","title":"Sea floor depth below geoid"},"source":{"type":"WMTS","url":"https://wmts.marine.copernicus.eu/teroWmts","layer":"GLOBAL_ANALYSISFORECAST_PHY_001_024/cmems_mod_glo_phy_anfc_0.083deg_static_202211--ext--bathy/deptho","style":"default","matrixSet":"EPSG:3857","projection":"EPSG:3857","tileGrid":{"tileSize":[128,128]},"dimensions":{}}}]},{"type":"Group","properties":{"id":"BaseLayersGroup","title":"Base Layers"},"layers":[{"type":"Tile","properties":{"id":"sx-cat_ortho680500;:;EPSG:3857","title":"Terrain Light Stereographic North"},"source":{"type":"TileWMS","url":"//sxcat-demo.eox.at/sxcat_maps/wms","projection":"ORTHO:680500","tileGrid":{"tileSize":[512,512]},"attributions":"{ Terrain light: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }","params":{"LAYERS":"sx-cat_ortho680500","TILED":true}}},{"type":"Tile","properties":{"id":"cloudless-2022;:;EPSG:3857","title":"EOxCloudless 2022"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/s2cloudless-2022_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ EOxCloudless 2022: \<a href=\\"//s2maps.eu\\" target=\\"_blank\\"\>Sentinel-2 cloudless - s2maps.eu\</a\> by \<a href=\\"//eox.at\\" target=\\"_blank\\"\>EOX IT Services GmbH\</a\> (Contains modified Copernicus Sentinel data 2022) }"}},{"type":"Tile","properties":{"id":"terrain-light;:;EPSG:3857","title":"Terrain light"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/terrain-light_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ Terrain light: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}},{"type":"Tile","properties":{"id":"eox-osm;:;EPSG:3857","title":"OSM Background"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/osm_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ OSM: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}}]}]' zoom="4" center=[-35.64662933349613,43.27388039326814] projection="" }--\>

\#\#\# AI-derived ice charts

Machine learning models developed by the Danish Meteorological Institute (DMI) interpret SAR and meteorological data to produce faster, scalable, and often higher-resolution ice charts. These can be compared side-by-side with traditional products in the CIF Dashboard.

\#\# map layer 3 \<!--{as="eox-map" style="width: 100%; height: 500px;" layers='[{"type":"Group","properties":{"id":"OverlayGroup","title":"Overlay Layers"},"layers":[{"type":"Tile","properties":{"id":"overlay_bright;:;EPSG:3857","title":"Overlay labels"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/overlay_base_bright_3857/default/g/{z}/{y}/{x}.png","projection":"EPSG:3857","attributions":"{ Overlay: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors, Made with Natural Earth, Rendering \&copy; \<a href=\\"//eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}}]},{"type":"Group","properties":{"id":"AnalysisGroup","title":"Data Layers"},"layers":[{"type":"Tile","properties":{"id":"sea_floor_depth;:;2017-01-01T00:00:00Z;:;wmts capabilities;:;EPSG:3857","title":"Sea floor depth below geoid"},"source":{"type":"WMTS","url":"https://wmts.marine.copernicus.eu/teroWmts","layer":"GLOBAL_ANALYSISFORECAST_PHY_001_024/cmems_mod_glo_phy_anfc_0.083deg_static_202211--ext--bathy/deptho","style":"default","matrixSet":"EPSG:3857","projection":"EPSG:3857","tileGrid":{"tileSize":[128,128]},"dimensions":{}}}]},{"type":"Group","properties":{"id":"BaseLayersGroup","title":"Base Layers"},"layers":[{"type":"Tile","properties":{"id":"sx-cat_ortho680500;:;EPSG:3857","title":"Terrain Light Stereographic North"},"source":{"type":"TileWMS","url":"//sxcat-demo.eox.at/sxcat_maps/wms","projection":"ORTHO:680500","tileGrid":{"tileSize":[512,512]},"attributions":"{ Terrain light: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }","params":{"LAYERS":"sx-cat_ortho680500","TILED":true}}},{"type":"Tile","properties":{"id":"cloudless-2022;:;EPSG:3857","title":"EOxCloudless 2022"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/s2cloudless-2022_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ EOxCloudless 2022: \<a href=\\"//s2maps.eu\\" target=\\"_blank\\"\>Sentinel-2 cloudless - s2maps.eu\</a\> by \<a href=\\"//eox.at\\" target=\\"_blank\\"\>EOX IT Services GmbH\</a\> (Contains modified Copernicus Sentinel data 2022) }"}},{"type":"Tile","properties":{"id":"terrain-light;:;EPSG:3857","title":"Terrain light"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/terrain-light_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ Terrain light: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}},{"type":"Tile","properties":{"id":"eox-osm;:;EPSG:3857","title":"OSM Background"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/osm_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ OSM: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}}]}]' zoom="4" center=[-35.64662933349613,43.27388039326814] projection="" }--\>

\#\#\# POLARIS risk index with Polar Code integration

The POLARIS algorithm combines ice chart data with a ship’s ice class rating to generate navigational risk scores. These help planners assess whether a ship can safely transit a given area, should proceed with caution, or should avoid it altogether. While not mandatory, POLARIS scores are often referenced by insurers in the event of an incident.

\#\# map layer 4 \<!--{as="eox-map" style="width: 100%; height: 500px;" layers='[{"type":"Group","properties":{"id":"OverlayGroup","title":"Overlay Layers"},"layers":[{"type":"Tile","properties":{"id":"overlay_bright;:;EPSG:3857","title":"Overlay labels"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/overlay_base_bright_3857/default/g/{z}/{y}/{x}.png","projection":"EPSG:3857","attributions":"{ Overlay: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors, Made with Natural Earth, Rendering \&copy; \<a href=\\"//eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}}]},{"type":"Group","properties":{"id":"AnalysisGroup","title":"Data Layers"},"layers":[{"type":"Tile","properties":{"id":"sea_floor_depth;:;2017-01-01T00:00:00Z;:;wmts capabilities;:;EPSG:3857","title":"Sea floor depth below geoid"},"source":{"type":"WMTS","url":"https://wmts.marine.copernicus.eu/teroWmts","layer":"GLOBAL_ANALYSISFORECAST_PHY_001_024/cmems_mod_glo_phy_anfc_0.083deg_static_202211--ext--bathy/deptho","style":"default","matrixSet":"EPSG:3857","projection":"EPSG:3857","tileGrid":{"tileSize":[128,128]},"dimensions":{}}}]},{"type":"Group","properties":{"id":"BaseLayersGroup","title":"Base Layers"},"layers":[{"type":"Tile","properties":{"id":"sx-cat_ortho680500;:;EPSG:3857","title":"Terrain Light Stereographic North"},"source":{"type":"TileWMS","url":"//sxcat-demo.eox.at/sxcat_maps/wms","projection":"ORTHO:680500","tileGrid":{"tileSize":[512,512]},"attributions":"{ Terrain light: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }","params":{"LAYERS":"sx-cat_ortho680500","TILED":true}}},{"type":"Tile","properties":{"id":"cloudless-2022;:;EPSG:3857","title":"EOxCloudless 2022"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/s2cloudless-2022_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ EOxCloudless 2022: \<a href=\\"//s2maps.eu\\" target=\\"_blank\\"\>Sentinel-2 cloudless - s2maps.eu\</a\> by \<a href=\\"//eox.at\\" target=\\"_blank\\"\>EOX IT Services GmbH\</a\> (Contains modified Copernicus Sentinel data 2022) }"}},{"type":"Tile","properties":{"id":"terrain-light;:;EPSG:3857","title":"Terrain light"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/terrain-light_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ Terrain light: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}},{"type":"Tile","properties":{"id":"eox-osm;:;EPSG:3857","title":"OSM Background"},"source":{"type":"XYZ","url":"//s2maps-tiles.eu/wmts/1.0.0/osm_3857/default/g/{z}/{y}/{x}.jpeg","projection":"EPSG:3857","attributions":"{ OSM: Data \&copy; \<a href=\\"http://www.openstreetmap.org/copyright\\" target=\\"_blank\\"\>OpenStreetMap\</a\> contributors and \<a href=\\"//maps.eox.at/\#data\\" target=\\"_blank\\"\>others\</a\>, Rendering \&copy; \<a href=\\"http://eox.at\\" target=\\"_blank\\"\>EOX\</a\> }"}}]}]' zoom="4" center=[-35.64662933349613,43.27388039326814] projection="" }--\>

\#\# Who Benefits

CIF’s Arctic shipping tools are designed for a range of users, including:

\* \*\*Commercial shipping companies\*\* moving goods into and out of Arctic regions, such as ore from Baffin Island or supplies for remote communities.

\* \*\*Tourism vessels\*\*, some of which are among the world’s most ice-capable ships, seeking immersive experiences in ice-covered waters.

\* \*\*Fishing fleets\*\*, often small and operating near the ice edge, where accurate, high-resolution ice data is critical.

\* \*\*Scientific research expeditions\*\*, including those aiming to reach high-latitude study sites or the North Pole, sometimes with icebreaker support.

\#\# Value and Impact

Value and Impact

By integrating multiple types of sea ice information into one tool, the CIF Dashboard supports:

\* Improved safety, through clearer visibility into route-specific ice risks

\* Better route planning, reducing delays, fuel use, and emissions

\* Compliance with the Polar Code, by providing easy access to required and recommended data

\* Faster, more informed decision-making, especially for time-sensitive or high-cost voyages

The CIF Dashboard offers a practical, scalable solution that increases Arctic data availability and accessibility, helping make it more usable by those navigating some of the world’s most challenging waters.

\#\# Value and Impact

Visit the CIF’s Beta Dashboard at https://cif.eox.at/ where you can find these and more tools to support the Arctic shipping sector, as well as tools for Aquaculture and Off-shore Renewable Energy.
