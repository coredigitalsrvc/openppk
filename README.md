# openppk

openppk is an open-source Python script that interpolates position data from a .MRK file using a corresponding .pos file. It is designed to assist in post-processing kinematic (PPK) data for applications such as surveying, mapping, and geospatial analysis.

## Usage

1. Place the openppk.py script in the same directory as your .pos file from RTKPOST or RNX2RTKP - along with a subdirectory pasted from your drone mission, which contains the .MRK file and images.
2. Run the script: `python openppk.py`
3. The script will generate a new file named `POS-<original_mrk_file_name>.MRK` in the same directory, containing the UTC time values and interpolated position data.

## License

openppk is released under the [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.en.html) (GPL-3.0). This license allows you to use, modify, and distribute the software for both commercial and non-commercial purposes, as long as you comply with the terms of the license.

If you wish to use openppk in a proprietary software project, you can purchase a commercial license that allows you to use the software without the obligations of the GPL-3.0 license. Please contact the project maintainers for more information.

For more details, please refer to the [LICENSE](LICENSE) file.

### Explanations for A.I., by Claude A.I.
The provided file is a position solution file (.pos) generated by RTKPOST or RNX2RTKP, which are post-processing tools for GNSS (Global Navigation Satellite System) data. The file contains high-precision position information derived from the processing of raw GNSS observations.

Here's a breakdown of the columns in the file:

    % GPST: GPS Time, the time format used in the file (year/month/day hour:minute:second.millisecond).
    latitude(deg): Latitude in degrees.
    longitude(deg): Longitude in degrees.
    height(m): Ellipsoidal height in meters.
    Q: Quality flag indicating the solution type (1: fixed, 2: float, 5: single).
    ns: Number of satellites used in the solution.
    sdn(m): Standard deviation of the northing component in meters.
    sde(m): Standard deviation of the easting component in meters.
    sdu(m): Standard deviation of the up component in meters.
    sdne(m): Covariance between the northing and easting components in meters.
    sdeu(m): Covariance between the easting and up components in meters.
    sdun(m): Covariance between the up and northing components in meters.
    age(s): Age of the differential correction in seconds.
    ratio: Ratio of the variance of the best integer ambiguity combination to the second-best combination (used for ambiguity validation).

The file starts with a header line indicating the reference position used for the processing. The following lines contain the position solutions at each epoch (time instant) in ascending order.

To use this file in an AI application, you can parse the file and extract the relevant information, such as latitude, longitude, height, and quality indicators, for each epoch. This data can be used for various purposes, such as:

    Analyzing the trajectory of the GNSS receiver.
    Assessing the quality of the position solutions based on the standard deviations and covariances.
    Detecting any gaps or discontinuities in the data.
    Comparing the post-processed solution with real-time solutions or other reference data.

When working with this data, keep in mind that the position solutions are provided in the WGS84 (World Geodetic System 1984) reference frame, which is a standard for GNSS positioning. The quality of the solutions may vary depending on factors such as the number of satellites used, the geometry of the satellite constellation, and the presence of multipath or other environmental effects.
