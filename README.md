# Project 4

Shamber Goldstein | March 13, 2020 | B ME 450 | Project 4: Hydrophone

## Introduction:

This projeProject 4's goal is to analyze noise in the ocean from wind, rain, mammal vocalization, air guns, and a volcanic eruption or earthquake [1]. These noises are possible to evaluate through the use of a hydrophone, "a passive acoustic sensor (an underwater microphone) that converts sound energy to electrical energy, with a binary stream output" [2]. The hydrophone raw data was extracted from the Ocean Obervatories Initiative (OOI) website [3] which allows the user to select an instrument, location, depth, date, and time for data collection. Part 1 of the project is to analyze the power spectral density (PSD) for the wind and rain readings at times when it is windy and not rainy, rainy and not windy, windy and rainy, and not windy or rainy. Plotting this against frequency, allows the user to analyze the effect of rain and wind on underwater noise. These plots are to be made for the Oregon shelf site and the Oregon offshore site. Part 2 of the project is to plot spectograms for times in the hydrophone data at any location that there is a marine mammal vocalization, and air gun noise, and a volcano eruption or earthquake, then compare their bandwidths with what is shown on the Wenz Curve (Figure 12). 

## Approach:

I began this project by importing in any neccessary packages. For this project, this included installing obspy. Using !pip to install obspy was not working on my computer, so I had to install it in my terminal using Homebrew. After installing obspy and the other necessary packages for the project, I began Part 1. 

I started Part 1 by creating a function that plots the power spectral density for each of the sites and time periods. Time periods were determined based on the results of Project 2 [5] which displayed when each location had the weather patterns mentioned in the introduction. The function uses the read in data to create a sampling rate as well as sliced portions of the data. It then uses this to calculate the PSD using Equation 1. The PSD and frequency were then normalized and converted as necessary for plotting by using Equation 2. Finally, the function plots the PSD converted to db and normalized against the normalized frequency. For each site and time period, their code read in the according hydrophone data then call the previously mentioned function with this the data as the input. The code would also individually title the plot with the according location and weather condition.

I began Part 2 with a function that plots a spectogram for each set of hydrophone data. It begins similarly to the function in Part 1, by creating sampling rates and slices of the data. The slices and sampling rates are used to calculate the overlap and the number of fast Fourier transform points (nFFT). It then uses the slices, nFFT, the sampling rates, and the number of overlap points in the built in mlab spectogram call to create data for the spectogram, frequency, and time. The spectogram data is then normalized and the three componenets are plotted together along with a colorbar key. This is the end of the function. For each noise evaluated in this part, their individual code reads in their data and calls the function to produce the spectogram. The code would also individually title the spectogram with the according noise source. The data for the mammal vocalization and airgun noise were taken at times specified by the instructor. The earthquake time and location I found myself. I did this by using the USGS website [6] to look at earthquakes around the latitude and longitude of one of the sites. I used the Oregon Offshore site. I then took the time and date of the earthquake closest to that location and got the hydrophone data at this time. 

## Results/Plots:

Figure 1: Power Spectral Density vs. Frequency for Oregon Shelf: Rainy, not Windy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-12%20at%202.41.20%20PM.png "R, n W, Shelf")

Figure 2: Power Spectral Density vs. Frequency for Oregon Shelf: Windy, not Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-12%20at%202.41.37%20PM.png "W, n R, Shelf")

Figure 3: Power Spectral Density vs. Frequency for Oregon Shelf: Windy and Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-12%20at%202.41.48%20PM.png "W, R, Shelf")

Figure 4: Power Spectral Density vs. Frequency for Oregon Shelf: Not Windy or Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-12%20at%202.42.01%20PM.png "n W, n R, Shelf")

Figure 5: Power Spectral Density vs. Frequency for Oregon Offshore: Rainy, not Windy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-12%20at%202.42.14%20PM.png "R, n W, Offshore")

Figure 6: Power Spectral Density vs. Frequency for Oregon Offshore: Windy, not Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-12%20at%202.42.29%20PM.png "W, n R, Offshore")

Figure 7: Power Spectral Density vs. Frequency for Oregon Offshore: Windy and Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-12%20at%202.42.41%20PM.png "W, R, Offshore")

Figure 8: Power Spectral Density vs. Frequency for Oregon Offshore: Not Windy or Rainy
![alt text](https://github.com/shamgold/Project4/blob/master/Screen%20Shot%202020-03-12%20at%202.42.54%20PM.png "n W, n R, Offshore")

Figure 9: Marine Mammal Vocalization Spectogram
![alt text](html "label")

Figure 10: Air Gun Noise Spectogram
![alt text](html "label")

Figure 11: Volcano Eruption/Earthquake Spectogram
![alt text](html "label")

## Analysis/Conclusions:

What is the effect of wind and rain on underwater noise? Explain any behavior you observe in your result. 

Which one has the highest impact? Rain or wind?

What are the main reasons for observing different spectral levels in Oregon shelf compared to Oregon offshore? 

The two sites are located in the same general locations but have very different depths. The Oregon shelf instrument has a depth of 80 m while the Oregon offshore instrument has a depth of 580 m. This means that looking at the effect of noise from rain and wind at these locations shows how these noises effect the ocean at shallow and deep depths. 

Compare the bandwidth of the three signals in Part 2. Are they consistent with what is shown in the Wenz curve?

## References:

Figure 12: Wenz Curve (for Reference)
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
