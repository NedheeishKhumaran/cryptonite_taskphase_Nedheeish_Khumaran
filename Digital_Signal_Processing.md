# Digital Signal Processing
## Definition
-	Digital signal processing (DSP) is a collection of techniques that use mathematical operations to improve the accuracy and reliability of digital communications. 
-	The process by which we could convert real world phenomena into digital data for analysis, manipulation and synthesis.
-	It is concerned with the representation of signals as a sequence of numbers or symbols and processing the sequence.
## Signal 
-	A signal is a function of information on the state or behavior of a physical quantity over other variables.
-	Considering the case of audio signals, we can plot the amplitude of the audio with respect to time. This is a signal.
### Continuous and Discreet signals
-	The above mentioned are two types of signals which are a matter of concern here. 
-	A continuous-time signal is defined for all points in time within a given interval, meaning it can take on values at any point on the time axis, on the other hand, a discrete-time signal is only defined at specific, discrete points in time, taking on values only at certain sampled intervals.
-	A `continuous-time` signal is like a smooth curve, whereas a `discrete-time` signal is like a series of points on a graph. 
-	A `continuous-time` signal has independent variable which can be a real number in the given range.
-	A `discrete-time` signal has independent variable which can only take integers according to its sample.
### Sampling
-	A continuous-time signal can be converted to discrete-time signal by a process called sampling.
-	The continuous-time signal’s value is measured at particular intervals of the independent variable (which depends on the number of samples) and plotted as discrete signal. 
-	This is an essential process for `Digital Signal Processing` since the computers can only work with discrete-time signals and not continuous-time signals. 
### Quantization
- Sampling helps us get discrete time intervals. The same way we need to discretize the magnitude of the signal for the same reason as above.
- We split the y-axis into convinient intervals and approximate the magnitude at a particular discrete interval to the nearest discrete magnitude.
- The quantisation can be done in different resolutions like 2 bits, 3 bits, 4 bits etc,. This affects the accuracy of the signal. 
- Higher its resolution (the number of bits), higher the accuracy of the signal to the original one.
### Binary Encoding
- The amplitudes obtained after quantization need to be encoded to binary numbers for the computer to be able to process, analyse and reconstruct the signal.
- If the signal has 8 discrete amplitudes, then we can encode them to 000,001,010,011...111.

## Transforms needed for processing
 After converting a continuous signal into discrete time signal, the motive is to analyse, process or store the signal.
For analysing and further processing the initial steps are to use various mathematical transforms to convert the signal from time domain to other domains like z domain, laplace domain, frequency domain etc.,.
The transform that we need to perform can be done using python with the help of its libraries like `numpy`, `scipy`, `pywt`,`sympy` etc
These can be plotted for visualisation by the help of `matplotlib.pyplot` library.

## Fourier Transform and its inverse
This helps in analysing the magnitude of a signal across the frequencies that exist in the signal. With this we can determine the actual signal (that has higher amplitude) and the noise frequencies (that have lower amplitudes).
Applying fourier transform for a huge signal can be computationally intensive. So we use an algorithm called `Fast Fourier Transform`. 
Python code: 

