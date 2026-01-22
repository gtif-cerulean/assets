The Harshness Index generates harshness maps based on wave height, sea
ice concentration, and iceberg density data. The user can set the
magnitude of each variable that is considered 'harsh' and the weight
that is given the variable.

A harshness/attractiveness index is a single parameter which combines
various data to provide an overall measure of the environmental
harshness or attractiveness of a region. In general, the index is given
by the following formula:

<img src="media/image1.emf" style="width:6.5in;height:0.47014in" />Where:

- V<sub>i</sub> is the i<sup>th</sup> variable

- W<sub>i</sub> is the weight assigned to the nth variable.
  <img src="media/image2.emf" style="width:1.26668in;height:0.48214in" />

- N<sub>i</sub> is the normalization factor for the i<sup>th</sup>
  variable – typically the largest expected value of V<sub>i</sub>.

The default harshness index used in the CIF is the Fleming-Drover
Harshness Index which takes into account:

- Mean annual number of days with a sea ice concentration greater than
  six-tenths (C)

- Mean annual number of days with a significant wave height greater than
  four meters (W)

- Mean annual open-water iceberg areal density (D)

Values for these parameters are normalized before incorporating them
into the Harshness Index calculation. In the cases of pack ice and
waves, the numbers of days exceeding the criteria were divided by 350
and 110, respectively. These values represent the approximate maximum
values expected. For iceberg density, the values were normalized (on
scale of 0 to 10) by calculating the logarithm of the iceberg density as
follows:

- For iceberg density of -6 (log of 10<sup>-6</sup> km<sup>-2</sup>) or
  lower, a value of 0

- For iceberg density of -1 (log of 10<sup>-1</sup> km<sup>-2</sup>), a
  value of 10

- Otherwise, a linear scaling between 0 and 10

The Fleming-Drover Harshness Index is given by the formula when:

- V<sub>1</sub> is the average number of days per year with a sea ice
  concentration \> 60%

- V<sub>2</sub> is the average number of days per year with a
  significant wave height \> 4 metres

- V<sub>3</sub> is the average annual iceberg density (number of
  icebergs per 100 km<sup>2</sup>)

- W<sub>1</sub> is 6

- W<sub>2</sub> is 2.5

- W<sub>3</sub> is 1.5

- N<sub>1</sub> is 350

- N<sub>2</sub> is 110

- N<sub>3</sub> is (12 + 2\*log<sub>10</sub>(V<sub>3</sub>))

- The iceberg density is within the given range

The harshness/attractiveness index can be customized to use other
variables and equations.

<img src="media/image3.emf" style="width:6.5in;height:0.53542in" />
