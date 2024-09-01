# Solar-Flare-Analysis-and-Prediction-Using-Clustering-and-Machine-Learning
This project focuses on the analysis of solar flares using data from the RHESSI mission. The objective is to cluster solar flares based on their characteristics and then use machine learning to predict the timing of peak flares. The analysis includes data preprocessing, feature engineering, clustering analysis, and time series prediction.

## Project Overview

Solar flares are intense bursts of radiation coming from the release of magnetic energy associated with sunspots. Understanding the patterns and predicting the behavior of solar flares is crucial for space weather forecasting and mitigating the effects of solar storms on Earth.

### Objectives:
1. **Cluster Analysis:** Group solar flares based on their characteristics (flare flags).
2. **Prediction:** Use machine learning models to predict the timing of the peak flare.

## Data

The dataset used in this project contains information about solar flares, including various flare flags, peak counts, and timing information. The data is sourced from the RHESSI mission, which provided detailed observations of solar flares.

### Key Features:
1. Peak Rate
- Definition: The peak count rate is the highest count rate observed during the flare in the energy range of 6-12 keV. This rate is averaged over the active collimators and includes background counts.
- Relevance: This metric helps to identify the intensity of the flare. A higher peak rate indicates a more intense flare.
  
2. Total Counts
- Definition: Total counts refer to the cumulative number of counts recorded in the 6-12 keV energy range over the duration of the flare. This is summed over all subcollimators and includes background counts.
- Relevance: Total counts provide an overall measure of the flare’s total energy output. Higher total counts suggest a more significant event.
  
3. Energy
- Definition: The energy value indicates the highest energy band in which the flare was observed. This is measured in kilo-electron volts (keV).
- Relevance: The energy level helps to classify the flare based on its energy emission. Different energy bands can reveal different aspects of the flare's behavior.
  
4. Radial Distance
- Definition: Radial distance is the distance from the center of the Sun to the flare’s position in the solar atmosphere.
- Relevance: This metric can help in understanding the spatial distribution of solar flares and their locations relative to the solar disk.

5. Quality Codes (Qn)
- Definition: Quality codes indicate the overall quality of the data for the event. The codes range from Q0 (highest quality) to Q11 (lowest quality), reflecting issues like data gaps, spacecraft anomalies, or particle contamination.
- Relevance: Higher quality codes (lower numbers) indicate more reliable data. It's important to consider these codes to ensure the accuracy of your analysis.
  
6. Active Region
- Definition: Active region is a number identifying the closest active solar region where the flare occurred, if available.
- Relevance: Active regions are areas of intense magnetic activity on the Sun. Knowing the active region can provide context for the flare’s origin and behavior.

7. Radial Offset
- Definition: Radial offset measures the distance of the flare’s position from the spacecraft's spin axis in arcseconds. This is used in spectroscopy to correct for the spacecraft's orientation.
- Relevance: This helps in accurately locating the flare’s position and can be crucial for detailed spectral analysis.

8. Peak Counts/Second (peak_c/s)
- Definition: Peak counts per second is the highest count rate measured in corrected counts during the flare.
- Relevance: This is similar to Peak Rate but specifically in terms of corrected counts, which might be adjusted for various factors to provide a more accurate measure.

9. Flare Flag Codes
   
a) a0 - In Attenuator State 0 (None) Sometime During Flare

- Explanation: The spacecraft was in the attenuator state "None" during the flare, meaning no attenuation was applied.
- Impact: The data is recorded with full sensitivity, which is usually ideal for accurate measurements.

b) a1 - In Attenuator State 1 (Thin) Sometime During Flare

- Explanation: The spacecraft was in the "Thin" attenuator state, which reduces the amount of incoming X-ray light.
- Impact: This state might be used to avoid detector saturation. It can affect the recorded intensity, so corrections may be needed.
  
c) a2 - In Attenuator State 2 (Thick) Sometime During Flare

- Explanation: The spacecraft was in the "Thick" attenuator state, significantly reducing X-ray light.
- Impact: The recorded data might underestimate the true intensity of the flare due to the heavy attenuation.
  
d) a3 - In Attenuator State 3 (Both) Sometime During Flare

- Explanation: The spacecraft was in a combined attenuator state, using both thin and thick attenuation.
- Impact: This can significantly reduce the sensitivity of measurements and might require careful calibration.
  
e) An - Attenuator State (0=None, 1=Thin, 2=Thick, 3=Both) at Peak of Flare

- Explanation: Indicates the attenuator state at the peak of the flare.
- Impact: Knowing the attenuator state at the peak helps in understanding the maximum observed intensity and correcting if needed.
  
f) DF - Front Segment Counts Were Decimated Sometime During Flare

- Explanation: Counts from the front segment of the detectors were decimated (reduced) during the flare.
- Impact: Data from this segment may be incomplete or less reliable due to decimation.
  
g) DR - Rear Segment Counts Were Decimated Sometime During Flare

- Explanation: Counts from the rear segment were decimated.
- Impact: Similar to DF, this can affect the reliability of data from the rear segment.
  
h) ED - Spacecraft Eclipse (Night) Sometime During Flare

- Explanation: The spacecraft was in the Earth’s shadow (eclipse) during part of the flare.
- Impact: The data might be affected by the lack of sunlight, leading to reduced sensitivity or inaccuracies.
  
i) EE - Flare Ended in Spacecraft Eclipse (Night)

- Explanation: The flare ended while the spacecraft was in eclipse.
- Impact: Data at the end of the flare might be incomplete or affected by the eclipse.
  
j) ES - Flare Started in Spacecraft Eclipse (Night)

- Explanation: The flare started while the spacecraft was in eclipse.
- Impact: Data at the beginning of the flare might be affected by the eclipse conditions.
  
k) FE - Flare Ongoing at End of File

- Explanation: The flare was still ongoing at the end of the data file.
- Impact: The data may not capture the complete end of the flare.
  
l) FR - In Fast Rate Mode

- Explanation: The spacecraft was operating in a fast rate mode during the flare.
- Impact: Fast rate mode can affect the sensitivity and timing resolution of the measurements.
  
m) FS - Flare Ongoing at Start of File

- Explanation: The flare was ongoing when the data file started.
- Impact: The initial part of the flare might be missing or incomplete.
  
n) GD - Data Gap During Flare

- Explanation: There was a gap in the data recording during the flare.
- Impact: Critical information may be missing, which can affect the analysis of the flare’s characteristics.
  
o) GE - Flare Ended in Data Gap

- Explanation: The flare ended while there was a data gap.
- Impact: The end of the flare might be poorly represented or missing in the data.
  
p) GS - Flare Started in Data Gap

- Explanation: The flare started during a data gap.
- Impact: The beginning of the flare might be poorly represented or missing in the data.
  
q) MR - Spacecraft in High-Latitude Zone During Flare

- Explanation: The spacecraft was in a high-latitude zone, which can affect measurements.
- Impact: Measurements might be influenced by higher radiation or other environmental factors in this zone.
  
r) NS - Non-Solar Event

- Explanation: The event is not related to solar activity.
- Impact: This indicates that the data should be excluded from solar flare analysis.
  
s) PE - Particle Event: Particles Are Present

- Explanation: Particles were detected during the flare.
- Impact: Particles can affect the detector's performance, leading to potential contamination in the data.
  
t) PS - Possible Solar Flare; In Front Detectors, but No Position

- Explanation: The event might be a solar flare, but the position could not be determined.
- Impact: This can affect spatial analysis, making it challenging to accurately locate the flare.
  
u) Pn - Position Quality: P0 = Position is NOT Valid, P1 = Position is Valid

- Explanation: Indicates whether the position of the flare is valid.
- Impact: P0 means position data should not be used, while P1 indicates reliable position data.
  
v) Qn - Data Quality: Q0 = Highest Quality, Q11 = Lowest Quality

- Explanation: Overall data quality, with lower numbers indicating better quality.
- Impact: Higher quality codes (lower numbers) mean more reliable data.
  
w) SD - Spacecraft Was in SAA Sometime During Flare

- Explanation: The spacecraft was in the South Atlantic Anomaly (SAA), an area with high radiation.
- Impact: Data from the SAA might be less reliable due to increased radiation.
  
x) SE - Flare Ended When Spacecraft Was in SAA

- Explanation: The flare ended while the spacecraft was in the SAA.
- Impact: The end of the flare data might be affected by SAA-related issues.
  
y) SS - Flare Started When Spacecraft Was in SAA

- Explanation: The flare started while the spacecraft was in the SAA.
- Impact: The beginning of the flare data might be affected by SAA-related issues.

## Results

- **Clustering Analysis:** The clustering revealed distinct groups of solar flares with similar characteristics. Cluster 1 was identified as having the highest number of flares, characterized by the flags A0 (no attenuation), P1 (valid position), and Q1 (high data quality).
  
- **Prediction:** The SVR model was the most effective in predicting the timing of peak flares, with a Mean Absolute Error (MAE) of 282.71 seconds, which translates to a prediction error of approximately 4.71 minutes.

## Conclusion

This project demonstrates the application of clustering and machine learning techniques in the analysis of solar flares. By grouping flares with similar characteristics and predicting their peak times, we gain insights that could be valuable for space weather forecasting and understanding solar flare behavior.

## Future Work

- **Refinement of Prediction Models:** Experiment with more complex models or ensemble methods to improve prediction accuracy.
- **Expanded Visualization:** Enhance Power BI dashboards to include more detailed insights and allow for greater interactivity.
- **Real-Time Prediction:** Explore the possibility of real-time prediction of flare peaks based on incoming data.
