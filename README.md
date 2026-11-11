
# 915 MHz Microstrip Patch Antenna
### Design, Simulation, Fabrication, and Experimental Validation

## Project Overview

This project focuses on the design, simulation, fabrication, and testing of a 915 MHz inset-fed rectangular microstrip patch antenna operating in the Industrial, Scientific, and Medical (ISM) frequency band.

The goal was to take an antenna from its initial analytical design through full-wave electromagnetic simulation, PCB layout, physical fabrication, and experimental validation.

The antenna was designed using transmission-line theory, modeled and optimized in Ansys HFSS, and implemented as a two-layer PCB using Altium Designer. Following fabrication, the antenna was tested using a NanoVNA-H to evaluate its input reflection coefficient (S11) and transmission performance (S21).

The project provided practical experience with RF design, impedance matching, electromagnetic simulation, PCB development, soldering, and RF test equipment.

## Tools and Equipment

**Software**
- Ansys HFSS — Electromagnetic simulation
- Altium Designer — PCB design and layout
- MATLAB / Python — Data analysis and visualization

**Hardware**
- NanoVNA-H Vector Network Analyzer
- Fabricated microstrip patch antenna PCBs
- Edge-mount SMA connectors
- Coaxial RF cables
- Soldering equipment

---

## 1. Antenna Design

### Design Specifications

The antenna was designed for operation near 915 MHz using a standard two-layer FR-4 PCB structure.

| Parameter | Value |
|---|---|
| Target Frequency | 915 MHz |
| Antenna Type | Rectangular Microstrip Patch |
| Feeding Method | Inset-Fed Microstrip |
| Target Input Impedance | 50 Ω |
| Substrate | Shengyi S1000H / TG150 FR-4 |
| Relative Permittivity | Approximately 4.6 |
| Loss Tangent | Approximately 0.011 |
| Substrate Thickness | Approximately 1.53 mm |
| Copper Thickness | 1 oz |
| PCB Layers | 2 |

### Analytical Design

The initial patch dimensions were calculated using the transmission-line model of a rectangular microstrip antenna.

The patch width was estimated using:

\[
W = \frac{c}{2f_r}\sqrt{\frac{2}{\epsilon_r+1}}
\]

The effective dielectric constant was approximated by:

\[
\epsilon_{eff} =
\frac{\epsilon_r+1}{2}
+
\frac{\epsilon_r-1}{2}
\left(1+\frac{12h}{W}\right)^{-1/2}
\]

The effective patch length was then calculated using:

\[
L_{eff} = \frac{c}{2f_r\sqrt{\epsilon_{eff}}}
\]

Fringing fields were accounted for using the length extension:

\[
\frac{\Delta L}{h} =
0.412
\frac{(\epsilon_{eff}+0.3)(W/h+0.264)}
{(\epsilon_{eff}-0.258)(W/h+0.8)}
\]

The physical patch length was estimated as:

\[
L = L_{eff}-2\Delta L
\]

These calculations provided the initial dimensions for electromagnetic simulation.

An inset-fed microstrip transmission line was selected to provide an impedance match near 50 Ω without requiring an external matching network.

---

## 2. Electromagnetic Simulation — Ansys HFSS

The antenna was modeled using Ansys HFSS to investigate its resonant frequency, impedance matching, and electromagnetic behavior.

The initial analytical dimensions provided a starting point, but additional optimization was necessary to approach the desired 915 MHz operating frequency.

The patch length and inset-feed geometry were adjusted to improve the antenna's resonance and input reflection coefficient.

### Simulation Process

1. Created the rectangular patch, dielectric substrate, and ground plane.
2. Modeled the inset-fed microstrip transmission line.
3. Assigned material properties and electromagnetic boundaries.
4. Configured the excitation and frequency sweep.
5. Evaluated the input reflection coefficient, S11.
6. Adjusted the antenna geometry to improve resonance and impedance matching.

### Initial Optimization

An earlier design iteration achieved:

| Parameter | Result |
|---|---|
| Simulated Resonant Frequency | 919.6 MHz |
| Simulated S11 | −16.92 dB |
| Patch Length | 7.53 cm |

This demonstrated that the analytical design and geometric optimization could produce a resonance close to the target frequency.

### Simulation Used for Experimental Comparison

The HFSS results used for the final comparison with the fabricated antenna showed:

| Parameter | Result |
|---|---|
| Simulated Resonant Frequency | 910.38 MHz |
| Simulated S11 Minimum | −11.64 dB |

These results were subsequently compared with the physical antenna measurements.

### HFSS Model

![HFSS Antenna Model](images/hfss_model.png)

*Figure 1. Three-dimensional HFSS model of the inset-fed microstrip patch antenna.*

### Simulated S11

![HFSS S11 Simulation](images/hfss_s11.png)

*Figure 2. Simulated input reflection coefficient obtained using Ansys HFSS.*

---

## 3. PCB Design and Fabrication

Following the simulation stage, the antenna was implemented as a two-layer PCB using Altium Designer.

The PCB layout included the rectangular radiating patch, inset-fed microstrip transmission line, ground plane, and edge-mount SMA connector.

Particular attention was given to maintaining the intended transmission-line geometry and providing a reliable ground connection at the SMA interface.

### PCB Design Considerations

- Maintained the antenna geometry established during simulation.
- Designed the microstrip feed for approximately 50 Ω characteristic impedance.
- Incorporated an edge-mount SMA connector for RF measurements.
- Added grounding connections and vias near the connector.
- Prepared manufacturing files for PCB fabrication.

### Altium PCB Layout

![Altium PCB Layout](images/altium_layout.png)

*Figure 3. Altium Designer PCB layout showing the antenna geometry, feed line, and SMA connector.*

### Fabricated Antennas

Five antenna PCBs were manufactured and assembled with SMA connectors.

![Fabricated Patch Antennas](Pics/Antennas.jpg)

*Figure 4. Five fabricated 915 MHz microstrip patch antennas with edge-mount SMA connectors.*

Fabricating multiple boards provided additional hardware for repeated measurements and antenna-to-antenna transmission testing.

---

## 4. Experimental S11 Measurements

After fabrication and assembly, the antenna was characterized using a NanoVNA-H vector network analyzer.

The primary objective was to measure the antenna's input reflection coefficient and compare its resonant behavior with the HFSS simulation.

S11 describes the reflection coefficient at the antenna input. It is useful for evaluating how effectively power is transferred from a 50 Ω source into the antenna.

The reflection coefficient is related to the input impedance by:

\[
\Gamma = \frac{Z_{in}-Z_0}{Z_{in}+Z_0}
\]

where:

- \(Z_{in}\) is the antenna input impedance.
- \(Z_0\) is the reference impedance, typically 50 Ω.

The logarithmic magnitude of S11 is expressed as:

\[
S_{11}(dB)=20\log_{10}|\Gamma|
\]

More negative S11 values indicate less reflected power and improved impedance matching.

### Measurement Procedure

1. Connected the NanoVNA-H to the antenna through an RF coaxial cable.
2. Calibrated the VNA for reflection measurements.
3. Performed a frequency sweep around the intended operating band.
4. Identified the frequency corresponding to the minimum S11 magnitude.
5. Exported the measured data for comparison with the HFSS simulation.

### Measured Results

| Parameter | Measured Result |
|---|---|
| Target Frequency | 915 MHz |
| Measured Resonant Frequency | 909.84 MHz |
| Measured S11 Minimum | −9.28 dB |
| Difference from Target | −5.16 MHz |

The fabricated antenna exhibited a clear resonance near the intended operating frequency.

Although the measured S11 minimum was not as low as the simulated result, the antenna demonstrated a recognizable resonant response.

---

## 5. Simulation vs. Measurement

One of the main objectives of this project was to evaluate how closely the physical antenna matched its electromagnetic simulation.

### S11 Comparison

![Simulated vs Measured S11](images/S11.png)

*Figure 5. Comparison of simulated and measured S11 responses for the fabricated patch antenna.*

### Results Summary

| Parameter | HFSS Simulation | Measurement |
|---|---|---|
| Resonant Frequency | 910.38 MHz | 909.84 MHz |
| Minimum S11 | −11.64 dB | −9.28 dB |
| Difference from 915 MHz | −4.62 MHz | −5.16 MHz |

The difference between the simulated and measured resonant frequencies was:

\[
\Delta f = |910.38-909.84| = 0.54\text{ MHz}
\]

This corresponds to a relative difference of approximately:

\[
\frac{0.54}{910.38}\times100\%
\approx 0.059\%
\]

The close agreement in resonant frequency suggests that the physical antenna's resonant behavior was reasonably well represented by the simulation.

However, the measured impedance match was weaker than predicted.

### Discussion

Several factors may contribute to differences between simulation and measurement:

- Manufacturing tolerances in the PCB geometry.
- Variations in the substrate dielectric properties.
- SMA connector and solder-joint parasitics.
- Differences between the modeled and physical feed structure.
- Measurement setup and calibration uncertainty.
- Nearby objects and environmental coupling.

The resonant frequency agreement was encouraging, but the difference in S11 magnitude indicates that the feed and impedance-matching behavior could benefit from further investigation.

An important lesson from this stage was that accurately predicting resonant frequency does not necessarily guarantee an equally accurate impedance match.

---

## 6. Antenna-to-Antenna Transmission Testing (S21)

In addition to measuring S11, a transmission experiment was performed using two fabricated patch antennas.

The purpose of this experiment was to observe RF transmission between the antennas and evaluate the frequency-dependent received signal.

S21 represents the forward transmission coefficient between two measurement ports:

\[
S_{21}(dB)=20\log_{10}|S_{21}|
\]

For this experiment, the measured S21 includes the combined effects of antenna coupling, propagation loss, antenna orientation, impedance mismatch, and the measurement environment.

### Transmission Measurement

![Measured S21](images/S21.png)

*Figure 6. Measured antenna-to-antenna S21 response using the fabricated patch antennas.*

### Results

The measured transmission response showed a peak of approximately:

**S21 ≈ −14.27 dB near 910 MHz**

The transmission peak occurred in the same general frequency region as the antenna's measured resonance.

This provided an additional experimental demonstration of RF transmission between the fabricated antennas.

### Interpretation

The S21 measurement demonstrated a frequency-dependent transmission response between the two antennas.

However, the measured value should not be interpreted as the gain of an individual antenna.

A calibrated antenna gain measurement would require additional information and a controlled measurement setup, including known antenna separation, orientation, reference antennas, and environmental conditions.

This experiment served as an initial communication-link test rather than a complete antenna radiation characterization.

---

## 7. Results and Key Takeaways

The project successfully progressed through the major stages of antenna development:

- Completed analytical calculations for a 915 MHz rectangular microstrip patch antenna.
- Developed and optimized the antenna model using Ansys HFSS.
- Created a manufacturable two-layer PCB using Altium Designer.
- Fabricated and assembled five physical antennas.
- Performed S11 measurements using a NanoVNA-H.
- Compared experimental results with electromagnetic simulation.
- Measured antenna-to-antenna S21 transmission.

### Key Results

| Metric | Result |
|---|---|
| Target Frequency | 915 MHz |
| Simulated Resonance | 910.38 MHz |
| Measured Resonance | 909.84 MHz |
| Resonance Difference | 0.54 MHz |
| Simulated S11 Minimum | −11.64 dB |
| Measured S11 Minimum | −9.28 dB |
| Measured S21 Peak | Approximately −14.27 dB |

### Engineering Lessons

The most valuable aspect of this project was gaining experience with the complete RF hardware development process.

Simulation provided a useful prediction of the antenna's resonant frequency, but experimental testing revealed differences in impedance matching that were not fully captured by the model.

The project also demonstrated the importance of PCB manufacturing tolerances, connector implementation, calibration, and repeatable measurement procedures.

These results provide a foundation for improving the design and developing more advanced RF communication systems.

---

## 8. Future Improvements

Several opportunities remain for expanding the project.

### Impedance Matching

Investigate the difference between simulated and measured S11 and improve the feed geometry or matching network to reduce reflections near 915 MHz.

### Radiation Pattern Measurements

Develop a controlled antenna measurement setup using a rotating platform or anechoic chamber to characterize the radiation pattern.

### Gain and Efficiency Characterization

Perform additional measurements to estimate antenna gain and investigate radiation efficiency.

### SDR Integration

Use a software-defined radio to receive and analyze signals transmitted between the fabricated antennas.

### Phased Array Development

Apply the experience gained from this project toward developing a multi-element phased array with electronically controlled beam steering.

---

## Project Status

**Completed:**
- Analytical antenna design
- HFSS simulation and optimization
- PCB layout and fabrication
- SMA connector assembly
- S11 measurement and simulation comparison
- Initial antenna-to-antenna S21 testing

**Future Work:**
- Impedance matching improvements
- Radiation pattern characterization
- SDR-based communication experiments
- Multi-element phased array implementation

---

## Author

**Josiah Germain**

Electrical Engineering — University of Houston

Focus Areas: RF Engineering, Antenna Design, Microwave Engineering, and Wireless Communications
