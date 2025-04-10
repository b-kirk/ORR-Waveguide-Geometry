# ORR-Waveguide-Geometry
Analysis of the effects of optical waveguide geometry on ring resonator behaviour - Third Year Individual Project at the University of Manchester

**Introduction**

This set of jupyter notebook/lab files were used to simulate a number of 2D ring resonator geometries in MEEP, the MIT Electromgnetic Equation Propagation software, used for optical waveguide simulation. These waveguides sweep values of gap sizes between waveguides for add-drop Optical Ring Resonators (ORRs), to analyse the effects on the output waveform intensity and wavelength on doing so. These optical geometries assume uniform control assigned to specific variables in the program and do not simulate real life materials, though this is possible using the MEEP library. 

This program contains the basis for not only sweeping gap sizes, but also radii, indices, and most other values controllable via MEEP, and so allows great versatility for future work so long as the desired output is fractional transmittance, which is computed as the ratio of intensity (Watt per meter squared) of detected straight waveguide output to the intensity of detected ring resonator output. 

**Demonstration**

A demonstration of the simulation other than verbally has not been included, as generally the program simply runs by executing the python program - with no user input required. To alter the variable iterated, an appropriate formula must be used, as shown in the variance of gap size as in the notebook, some alike:

$$w_{gap, i} = w_{offset}+w_{unit}\times\frac{i_{gap}+1}{N}$$

which iterates individual values of $w_{gap, i}$ for a range $w_{unit}$, dividing this range into i elements. $w_{offset}$ is then used to increment manually to capture a new range past the maximum of $w_{unit}$.

**User Installation Instructions**

The powerpoint supplied to Dr. Huanqing Ye of the University of Manchester Photon Science Institute as to installation procedure has been included in this repository, and may be followed as the procedure for installation.

A note on this powerpoint is that it mentions use of jupyter notebook, however replacing 'jupyter notebook' with 'jupyter lab' gives the much more fleshed out jupyter lab interface, similar to something like Visual Studio Code.

**Other Technical Details**

Within this program, chosen radius was not arbitrary, and was in fact calculated to cause ORR resonance at 1550 nm wavelength within the medium, via the equation:

$$\frac{2\pi \times n_{eff}}{\lambda_{res}}\times L = 2\pi\times m,\quad L=\frac{\lambda_{res}}{n_{eff}}\times m, \quad R=\frac{\lambda_{res}}{2\pi\times n_{eff}}\times m$$

In the above equation, R represents therefore the radius of the Ring Resonator, L the total path length ($L=2\pi R$), $n_{eff}$ the effective index (assumed to be the geometry index), and $\lambda_{res}$ the resonant wavelength (1550 nm) of the ring.

This repository also contains the second program, for a double ring setup, which changes only the size of the cell, and offsets now two rings to be at a distance $r_{offset}$ from the origin, equal to some arbitrary gap between the two rings plus the radius of the ring. Two rings are simulation via defining a second ring at different position, with elsewise completely the same parameters. The gap size is still altered as above, as the formula holds for two rings. 

Finally, as demonstrated in the second segment of each notebook, the plot may be altered and reconfigured to represent a desired area for analysis, and via typical pyplot means may be altered in title and axes. Once run, this segment saves the CSV file for each wavelength/transmittance graph produced by iterating the main loop, and produces one final figure of each iteration placed onto a single graph.

**Known Issues/Possible Improvements**

The program has variable 'frames' intended to be used to produce animations natively in the jupyter notebook file, to be saved to the device, instead of producing a gif via Linux CLI tools using many individual frames. This was not completed, as the manner in which figures are produced interacting with MEEP's own functions caused some errors. It was found that no animations were particularly needed for the final results, and so this feature was sidelines, but likely could be implemented with some effort. 

This program could be converted for MEEP's support of GPU procesisng, in order to possibly decrease computation time, which could therefore allow more precise data or more iterations, in less time.

As a small note, the uploaded file for the double ring states that the graph is for 0.6-1.0 micrometers, but is in fact 0.1-0.5 micrometers by the formula, the title was simply not manually updated.

