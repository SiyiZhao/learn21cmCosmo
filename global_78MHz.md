

### data analysis pipeline :
- filtering for *data quality* and radio-frequency interference (*RFI*) .
- get the spectrum **dominated by Galactic synchrotron emission**. (a).
- fitting and removing *the foreground model*. get the residuals (b). 
- fitting the 21-cm models. get the residuals (c). 
- get the recovered model profile (d).  **with a signal-to-noise ratio of 37, amplitude of 0.53 K, centre frequency of 78.1 MHz and width of 18.7 MHz.**
- the sum of the model and residuals (e).


### results:

![[EDGES3data.png]]  
Fig.1. in [[@bowman2018edges3|Bowman et al., 2018]]

### best fit

![[EDGES3fit.png]]
Fig.2. in [[@bowman2018edges3|Bowman et al., 2018]]

- “black line is the model fit for the hardware and analysis configuration with the highest signal-to-noise ratio (equal to 52; H2;” (Bowman et al., 2018, p. 2)
	- “processed using 60–99 MHz and a four-term polynomial (see equation (2) in Methods) for the foreground model.” (Bowman et al., 2018, p. 2)
- H8 = Fig.1.(e)
	- “uses the same data as for the thick black line (H2), but a different foreground model and the full frequency band.” (Bowman et al., 2018, p. 2)

### instrument 
[[EDGES3photo.png]]


## Questions 

电离层会影响 foreground 的 smooth。
“The ionosphere further complicates chromatic mixing.” (Shen et al., 2021, p. 1)
- “The most significant propagation effects relevant to the sky-averaged spectra are **absorption and refraction**.” (Shen et al., 2021, p. 1)
- “These effects increase with decreasing frequency, which scale approximately as 𝜈^-2, and are 2-3 orders of magnitude larger than the global 21-cm signal” (Shen et al., 2021, p. 1)

Shen et al., 2021
![[Pasted image 20220606154007.png]]
show that the ionosphere will 
![[Pasted image 20220606145452.png]]

“It suggests that the D-layer has a greater effect on the overall chromatic variance of the integrated antenna temperature.” (Shen et al., 2021, p. 5)
![[Pasted image 20220606150716.png]]