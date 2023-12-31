# Decay chain

The [FIRST STEPS](../THAT_First_Steps.pdf) describes in chapter 9.1 Radioactive decay model.

This can be easily expanded in Decay chain, where the first emelemnt N1 decays into element N2, which also decays.

The model is described by equations:

dN1/dt = -k1 * N1

dN2/dt = k1 * N1 - k2 * N2

This translates directly to schematics![schematics](schematics.jpg). Notice that we need to add inverter for - k2*N2(t) branch as summer implicitly inverts its output. 

and wiring ![wiring](wiring.jpg)

Dynamics of the system:

yellow: N1(t), N1(t=0) = +1 (THAT units)

blue:   N2(t), N2(t=0) = 0  (THAT units)

Sample waveforms:

![01_decay_chain_2_elements](01_decay_chain_2_elements.png)
![02_decay_chain_2_elements](02_decay_chain_2_elements.png)
![03_decay_chain_2_elements](03_decay_chain_2_elements.png)
![04_decay_chain_2_elements](04_decay_chain_2_elements.png)
![05_decay_chain_2_elements](05_decay_chain_2_elements.png)

## 3 transient elements (plus final element)

Further expansion to 3 transient elemenents (plus final element) is straightforward. We simply add the equation:

dN3/dt = k2 * N2 - k3 * N3

and connect it via summer to the exisitng circuit the same way, as we have added circuit for N2(t) in previous step. See schematics: ![schematics3](schematics_3_elements.jpg).

![wiring3](wiring_3_elements.jpg)

Picture above shows the sample implementation. Since I have only 2 channel oscilloscope available, only N2(t) (blue) and N3(t) (yellow) are displayed. Coefficients 1-3 are set to emulate this scenario:
* N1 - fast decay (coeff 1 = 0.58)
* N2 - intermediate decay speed (coeff 2 = 0.45)
* N3 - slow decay speed (coeff 3 = 0.11) 

* Notice how element N3 (yellow) builds up, surpassing the amount of element N2, before decaying into the final product.

![01_decay_chain_3_elements.png](01_decay_chain_3_elements.png)

Compare it against the [analytical solution.](https://www.geogebra.org/m/pzeu65am) N1 (initial element, green) and N4 (final element, magenta) are also displayed. N2 (blue) and N3 (yellow) are drawn in the same color as on the oscilloscope. 

![01_decay_chain_3_elements_exact_solution.png](01_decay_chain_3_elements_exact_solution.png)

I have overlayed the picture from the oscilloscope over the exact solution - as you can see, there is almost a perfect match for N2 and N3 dynamics. Both curves are very hard to distinguish apart.

![01_decay_chain_3_elements_compare.png](01_decay_chain_3_elements_compare.png)
