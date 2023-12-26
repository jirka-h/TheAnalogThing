# Decay chain

The [FIRST STEPS](../THAT_First_Steps.pdf) describes in chapter 9.1 Radioactive decay model.

This can be easily expanded in Decay chain, where the first emelemnt N1 decays into element N2, which also decays.

The model is described by equations:

dN1/dt = -k1 * N1

dN2/dt = -dN1/dt - k2 * N2

This translates directly to schematics![schematics](schematics.jpg).

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


