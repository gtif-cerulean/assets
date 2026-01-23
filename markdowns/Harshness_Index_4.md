The Harshness Index generates harshness maps based on wave height, sea ice concentration, and iceberg density data. The user can set the magnitude of each variable that is considered 'harsh' and the weight that is given the variable.

A harshness/attractiveness index is a single parameter which combines various data to provide an overall measure of the environmental harshness or attractiveness of a region. In general, the index is given by the following formula:

![](Harshness_EQ1.png)

Where:

-   Vi is the ith variable
-   Wi is the weight assigned to the nth variable. ![](Harshness_EQ2.png)
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
