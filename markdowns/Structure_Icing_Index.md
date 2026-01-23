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
