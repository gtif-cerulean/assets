There can be a long wait for the next satellite image to be received during which sea ice can move a considerable distance. The Sea Ice Motion Animation algorithm transforms a satellite image using a sea ice drift forecast to simulate what the ice in a region should look like in the future. The algorithm uses the neXtSIM model for ice drift forecasts up to six hours ahead.

The neXtSIM model is a lagrangian sea ice model designed to address the challenges posed by the highly non-linear and evolving dynamics of Arctic sea ice. It employs an elasto-brittle rheology to capture the fracturing and deformation of sea ice with high fidelity. The model is forced with atmospheric and oceanic inputs from ECMWF and TOPAZ5 respectively and provides detailed forecasts of variables such as ice concentration, thickness, and most importantly, the sea ice drift in u and v components, which is used in the sea ice motion animation.

The following parameters are defined by the user:

-   forecast duration: Number of hours the forecast should run, starting at the timestamp of the input image file,
-   GCP separation: The maximum distance in pixels between the ground control points automatically set throughout the image.

By default, ground control points (GCPs) are set in the four corners of the image. However, the number of GCPs can be increased, placing more points across the image and hence increasing the resolution of the following image warping. The procedure uses an hourly time step, until the forecast reaches the end of the forecast time window. The transformation of the image is performed by the Thin Plate Spline (TPS) algorithm, which is a mathematical model used for non-rigid image alignment and deformation, offering a smooth mapping between points in two-dimensional space. It operates by minimizing the bending energy of a smooth surface that passes through a set of control points, making it ideal for warping applications.
