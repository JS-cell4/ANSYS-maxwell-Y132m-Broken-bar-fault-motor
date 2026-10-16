# Broken Rotor Bar Fault Analysis of a Y132M Induction Motor (Ansys Maxwell)

Finite-element study of a Y132M three-phase, 4-pole, 7.5 kW (10 hp) squirrel-cage
induction motor with 'induced broken rotor bar faults', built in 'Ansys Maxwell'.
The healthy motor model is used as the baseline, and the fault is introduced by
breaking one or more rotor bars. The 2D transient model is also fed into
'Maxwell 3D' to study the instantaneous response, including end effects.

## Overview

Broken rotor bars are one of the most common rotor faults in induction motors.
They distort the air-gap flux, cause torque and speed oscillations, and add
characteristic sidebands to the stator current spectrum. This project compares
the 'healthy' and 'faulty' motor so the fault signature can be observed and
used for condition monitoring and fault diagnosis research.

## Motor Specifications
 

 Frame / type - Y132M, three-phase squirrel-cage induction motor 
- Rated power : 7.5 kW (10 hp) 
- Poles - 4 
- Synchronous speed : 1600 rpm 
- Rated slip : 0.04 (4 %) 
- Rated rotor speed  ~1536 rpm (Ns x (1 - s)) 
- Approx. rated shaft torque - ~46.6 N·m (P / omega) 

## Simulation Setup

### Maxwell 2D
- Solution type: Magnetic > Transient
- Geometry mode: Cartesian, XY
- Stator and rotor with slots, three-phase winding and rotor bars
- Rotational motion band with the rotor speed set from the slip

## Fault Modelling
- Healthy case: all rotor bars intact (baseline)
- Fault cases: one, two or more adjacent bars broken
- A broken bar is modelled by replacing the bar material with a
  high-resistivity material (or air), so it carries no current
- Same load, supply and slip used in every case for a fair comparison

### Maxwell 3D
- The model is fed into Maxwell 3D for the instantaneous transient response
- End rings and end-winding effects are included

## Results and Analysis
- Instantaneous electromagnetic torque: healthy vs. faulty (torque ripple increase)
- Speed oscillation under fault
- Stator phase currents and their FFT spectrum
- Rotor bar currents (zero in the broken bar, higher in neighbouring bars)
- Flux density distribution and air-gap flux asymmetry

### Fault signature (MCSA)
Broken bars produce sidebands around the supply frequency at

    f_sb = (1 ± 2s) · f_supply

where s is the slip. Check for these sidebands in the stator current spectrum.

## Requirements
- Ansys Electronics Desktop (Maxwell 2D / 3D)
- Transient solver licence
- MATLAB or Python (optional) for FFT post-processing of exported data

## How to Run
1. Clone the repository.
2. Open the `.aedt` project in Ansys Electronics Desktop.
3. Run the **healthy** design first and record the results.
4. Run the **broken bar** design(s).
5. Export torque and current data, then compare and plot the FFT spectra.



## Related Work
- Y132M healthy induction motor transient FEA (add repository link)
- Simulink SPWM inverter-fed induction motor drive (add repository link)

## Possible Extensions
- Increasing the number of broken bars and comparing severity
- Broken end-ring fault and rotor eccentricity
- Inverter-fed supply through Twin Builder co-simulation
- Machine-learning fault classification using the simulated current data

