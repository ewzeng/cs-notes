today: intro to color science

spectral power distribution: amount of light at each wavelength

light detection: measured signal = $\int$  (input spectrum) $\times$ (detector sensitivity). can be discretized into dot product

cone cells: only 3 types (S, M, L), each with different detector sensitivities. thus eyes convert spectrum ($\infty$-dim) to 3-dim value. as a result, there exists metamers: different spectra that elicit same S, M, L response. (reason why mixing colors can get other colors)

R, G, B are each just a specific defined spectrum

color reproduction problem: at each pixel, choose R, G, B so output color matches appearance of color in real world

- after discretizing the spectrum, just matrix multiplications: $RGB = (M_{SML}M_{RGB})^{-1}M_{SML} (spectrum)$

- color reproduction issue: what if get negative numbers for RGB? too bad. "out of gamut"