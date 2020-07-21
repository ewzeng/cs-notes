jaggies is an example of a general problem (aliasing) in sampling

aliasing = sampling error (due to low sampling rate)

anti-aliasing ideas: 

- filter out high frequencies b4 sample (filter = convolution)
- sample at higher frequency (Shannon thm + Nyquist frequency)

combining these two ideas: filter out above Nyquist frequency

for jaggies, can pre-filter with 1 pixel box (removes much of above Nyguist if sample per pixel) and then sample

- same as computing avg over a pixel; thus can be approximated by supersampling multiple points inside a pixel and then averaging