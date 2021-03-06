```python
import matplotlib.pyplot as plt
import numpy as np
```

# Numpy fft
Usage of [Numpy fft](https://numpy.org/doc/stable/reference/routines.fft.html#module-numpy.fft) for real data


```python
t = np.arange(0,2,0.01) # 2 seconds, 100 measurements per second
freq1 = 4 # 4 hz
freq2 = 10 # 10 hz
y = 1 + 0.8 * np.sin(2 * np.pi * t * freq1) + 0.3 * np.sin(2 * np.pi * t * freq2)
N = t.shape[-1]
print(N) # N measurement points
plt.plot(t, y)
```

    200





    [<matplotlib.lines.Line2D at 0x7f7ba6161ca0>]




    
![svg](numpy-fft_files/numpy-fft_2_2.svg)
    


# Vizualize the signal main frequencies
- Compute the fourier transform
- Numpy fftfreq helper computes the various frequencies (rfftfreq for real, no negative frequencies)
- Plot the fft against the frequencies
- The spike a f=0 is the main amplitude of the signal
- Smaller spikes at f=4 and f=10 Hz with amplitudes 0.8 and 0.3
- TODO: The amplitude for f=4 and f=10 is off by a factor 2, explain (maybe due to rfft not having the negative frequencies that would sum up ?)


```python
fft = np.fft.rfft(y)

freq = np.fft.rfftfreq(N, d=0.01)
plt.plot(freq, abs(fft)/N)
plt.plot(0, 0, marker='o', markersize=5, color="red")
plt.plot(freq1, 0, marker='o', markersize=5, color="red")
plt.plot(freq2, 0, marker='o', markersize=5, color="red")
```




    [<matplotlib.lines.Line2D at 0x7f7ba5c61f10>]




    
![svg](numpy-fft_files/numpy-fft_4_1.svg)
    


# Retrieve the original signal
- Compute the inverse fft with numpy ifft function


```python
inverse_fft = np.fft.irfft(fft)

plt.plot(t, inverse_fft)
```




    [<matplotlib.lines.Line2D at 0x7f7ba5c402e0>]




    
![svg](numpy-fft_files/numpy-fft_6_1.svg)
    

