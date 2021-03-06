# Project 4

Shamber Goldstein | March 13, 2020 | B ME 450 | Project 4: Hydrophone

## Introduction:

Project 4's goal is to analyze noise in the ocean from wind, rain, mammal vocalization, air guns, and a volcanic eruption or earthquake [1]. These noises are possible to evaluate through the use of a hydrophone, "a passive acoustic sensor (an underwater microphone) that converts sound energy to electrical energy, with a binary stream output" [2]. The hydrophone raw data was extracted from the Ocean Obervatories Initiative (OOI) website [3] which allows the user to select an instrument, location, depth, date, and time for data collection. Part 1 of the project is to analyze the power spectral density (PSD) for the wind and rain readings at times when it is windy and not rainy, rainy and not windy, windy and rainy, and not windy or rainy. Plotting this against frequency, allows the user to analyze the effect of rain and wind on underwater noise. These plots are to be made for the Oregon shelf site and the Oregon offshore site. Part 2 of the project is to plot spectograms for times in the hydrophone data at any location that there is a marine mammal vocalization, and air gun noise, and a volcano eruption or earthquake, then compare their bandwidths with what is shown on the Wenz Curve (Figure 12). 

## Approach:

I began this project by importing in any neccessary packages. For this project, this included installing obspy. Using !pip to install obspy was not working on my computer, so I had to install it in my terminal using Homebrew. After installing obspy and the other necessary packages for the project, I began Part 1. 

I started Part 1 by creating a function that plots the power spectral density for each of the sites and time periods. Time periods were determined based on the results of Project 2 [5] which displayed when each location had the weather patterns mentioned in the introduction. The function uses the read in data to create a sampling rate as well as a sliced portion of the data to work with. It then uses this to calculate the PSD using Equation 1. The PSD and frequency were then normalized and converted as necessary for plotting by using Equation 2. Finally, the function plots the PSD converted to db and normalized against the normalized frequency. For each site and time period, their code read in the according hydrophone data then call the previously mentioned function with this the data as the input. The code would also individually title the plot with the according location and weather condition.

I began Part 2 with a function that plots a spectogram for each set of hydrophone data. It begins similarly to the function in Part 1, by creating sampling rates and a slice of the data to work with. The sliced data portion and sampling rates are used to calculate the overlap and the number of fast Fourier transform points (nFFT). It then uses the slice, nFFT, the sampling rates, and the number of overlap points in the built in mlab spectogram call to create data for the spectogram, frequency, and time. The spectogram data is then normalized and the three componenets are plotted together along with a colorbar key. This is the end of the function. For each noise evaluated in this part, their individual code reads in their data and calls the function to produce the spectogram. The call takes the input of the data file, start time in the data, time the data should plot and analyze, and the frequency y-axis limit. The code would also individually title the spectogram with the according noise source. The data for the mammal vocalization and airgun noise were taken at times specified by the instructor. The earthquake time and location I found myself. I did this by using the USGS website [6] to look at earthquakes around the latitude and longitude of one of the sites. I used the Oregon Offshore site. I then took the time and date of the earthquake closest to that location and got the hydrophone data at this time. 

## Results/Plots:

Figure 1: Power Spectral Density vs. Frequency for Oregon Shelf: Rainy, not Windy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-13%20at%205.12.12%20PM.png "R, n W, Shelf")

Figure 2: Power Spectral Density vs. Frequency for Oregon Shelf: Windy, not Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-13%20at%205.12.20%20PM.png "W, n R, Shelf")

Figure 3: Power Spectral Density vs. Frequency for Oregon Shelf: Windy and Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-13%20at%205.12.30%20PM.png "W, R, Shelf")

Figure 4: Power Spectral Density vs. Frequency for Oregon Shelf: Not Windy or Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-13%20at%205.12.39%20PM.png "n W, n R, Shelf")

Figure 5: Power Spectral Density vs. Frequency for Oregon Offshore: Rainy, not Windy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-13%20at%205.12.47%20PM.png "R, n W, Offshore")

Figure 6: Power Spectral Density vs. Frequency for Oregon Offshore: Windy, not Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-13%20at%205.12.55%20PM.png "W, n R, Offshore")

Figure 7: Power Spectral Density vs. Frequency for Oregon Offshore: Windy and Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-13%20at%205.13.04%20PM.png "W, R, Offshore")

Figure 8: Power Spectral Density vs. Frequency for Oregon Offshore: Not Windy or Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-13%20at%205.13.13%20PM.png "n W, n R, Offshore")

Figure 9: Marine Mammal Vocalization Spectrogram
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-13%20at%206.24.58%20PM.png "mammal vocalization")

Figure 10: Airgun Noise Spectrogram                                  
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-13%20at%206.25.09%20PM.png "airgun noise")

Figure 11: Earthquake Spectrogram                                   

![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-13%20at%206.56.35%20PM.png "earthquake")

## Analysis/Conclusions:

##### What is the effect of wind and rain on underwater noise? Explain any behavior you observe in your result. 

At the Shelf site, in shallower water, when rain or wind are heavy independantly of each other they appear to increase the PSD of the noise in the water. However, when they occur at the same time they don't have much of an effect. In the deeper water, at the Offshore site, the rain and wind don't appear to effect the overall level of PSD. Instead they seem to decrease the range of values, centralizing them closer to the mean at each frequency range.

Determining a correlation between the individual effects of wind and rain on noise is difficult with my data set due to the different findings in the locations. However, through online research I was able to find a more clear answer: rain and wind increase the PSD underwater. I was also able to look more in depth online and I found that there's a exponential trend where lower frequencies increase with wind speed, while higher frequencies increase slightly or remain the same [7]. This research allowed me to attribute the increase in lower frequencies in the Oregon Shelf: Windy but not Rainy plot to the increased wind speed. I also found that rain noise is a result of drops hitting the surface as well as the bubbles they create and depends on the bubble size. Smaller drops produce high frequency noise in the range of 13-25 kHz and large drops make noise as low as 1 kHz[8]. This explains the spikes between 10 and 15 kHz on the Oregon Shelf plots with rainfall. 

##### Which one has the highest impact? Rain or wind?

Rain appears to have a higher impact on underwater noise. At the Oregon Shelf site, the rain increases the PSD underwater much more than the wind does. At the Oregon offshore site, the wind doesn't appear to change much while the rain decreases the range of PSD values while keeping the mean level about the same. Rain also creates spikes in certain frequencies, the increase in PSD isn't as significant and only affects that frequency as opposed to the entire curve.

##### What are the main reasons for observing different spectral levels in Oregon shelf compared to Oregon offshore? 

The two sites are located in the same general locations but have very different depths. The Oregon shelf instrument has a depth of 80 m while the Oregon offshore instrument has a depth of 580 m. This means that looking at the effect of noise from rain and wind at these locations shows how these noises effect the ocean at shallow and deep depths. This can be important when evaluating how noise could effect life underwater at different depths.

##### Compare the bandwidth of the three signals in Part 2. Are they consistent with what is shown in the Wenz curve?

The marine mammal vocalization signal reached above 2 kHz, the airgun was lower at up to 200 Hz, and the earthquake was only up to 100 Hz. The Wenz curve (Figure 12) shows the frequency ranges of various sources of ocean noise. Marine mammal vocalization falls under the "biologics" category which hich extends from 10 Hz to 100,000 Hz. My data for a marine mammal call falls into the range. Airgun sounds most likely fall under the industrial activity category, which ranges from 10 Hz to 10,000 Hz. My airgun data fits in this range. It should be noted however, that the SPL of the airgun blasts are beyond the that of industrial and ship noise. This is likely because airgun blasts are intentionally designed to be extraordinarily loud, compared to ships and drilling rigs which may have acoustic dampening measures in place. Earthquakes, which are individually labeled in the Wenz curve, range from 0 to 100 Hz with a peak SPL of over 120 dB at 10 Hz. This fits perfectly with my data, which has peaks of 128 dB between 0 and 40 Hz. Therefore, according all of my signal bandwidths are consistent with what is shown on the Wenz Curve.

## References:

Figure 12: Wenz Curve                                 
![alt text](https://github.com/shamgold/Project4/blob/master/Wentz-ambient-jm2013-600.png "Wenz Curve")

Equation 1: PSD                                   
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-12%20at%203.16.14%20PM.png "PSD Equation")

Equation 2: PSD Normalization and Conversion
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-12%20at%203.18.47%20PM.png "PSD Norm and Conv")

[1] Shima Abadi. In Class Lecture – Ocean Noise. [26 Feb. 2020].

[2] Ocean Observatories Initiative. 2020. HYDBB. [online] Available at: <https://oceanobservatories.org/instrument-class/hydbb/> [Accessed 12 March 2020].

[3] Ocean Observatories Initiative. 2020. HYDBBA. [online] Available at: <https://oceanobservatories.org/instrument-series/hydbba/> [Accessed 12 March 2020].

[4] Discovery of Sound in the Sea. 2020. What Are Common Underwater Sounds?. [online] Available at: <https://dosits.org/science/sounds-in-the-sea/what-are-common-underwater-sounds/> [Accessed 12 March 2020].

[5] Project 2: https://github.com/shamgold/Project-2

[6] Earthquake.usgs.gov. 2020. M 3.9 - 43Km W Of Waldport, Oregon. [online] Available at: <https://earthquake.usgs.gov/earthquakes/eventpage/us10008hwk/executive> [Accessed 13 March 2020].

[7] S. S. Murugan, “Noise Model Analysis and Estimation of Effect due to Wind Driven Ambient Noise in Shallow Water,” International Journal of Oceanography, Dec. 2011.

[8] J. A. Nystuen, “Listening to Raindrops from Underwater: An Acoustic Disdrometer,” Journal of Atmospheric and Oceanic Technology, Mar. 2001.
