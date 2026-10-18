
# 915 MHz Inset-Fed Microstrip Patch Antenna

**RF Engineering | Antenna Design | Ansys HFSS | Impedance Matching | Altium Designer**

## Project Overview

This project focuses on the analytical design, electromagnetic simulation, and PCB implementation of a **915 MHz rectangular microstrip patch antenna**.

The primary goal was to gain practical experience in RF antenna design by applying transmission-line and microstrip antenna theory, validating the analytical design through full-wave electromagnetic simulation, and translating the optimized geometry into a manufacturable printed circuit board.

The project also serves as the first stage of a larger personal goal: developing a wireless communication system that can eventually support digital modulation and more advanced antenna configurations.

The antenna was designed for operation near the **915 MHz ISM band** using an inset-fed microstrip transmission line and an FR-4-based PCB substrate.


## Project Visuals

### Simulated Return Loss

<p align="center">
  <img src="HFSS%20Simulation/Patch_Antenna_S11.png"
       alt="HFSS simulated S11 response"
       width="700">
</p>

**Figure 1.** Simulated input reflection coefficient
showing resonance at 919.6 MHz with S11 = -16.92 dB.

### HFSS Antenna Geometry

<p align="center">
  <img src="HFSS%20Simulation/HFSS_Model.png"
       alt="Inset-fed microstrip patch antenna modeled in HFSS"
       width="700">
</p>

**Figure 2.** Three-dimensional HFSS model of the
inset-fed rectangular patch antenna.

### Altium PCB Layout

<p align="center">
  <img src="PCB/PCB_Layout.png"
       alt="Two-layer antenna PCB layout in Altium"
       width="700">
</p>

**Figure 3.** PCB layout transferring the optimized
antenna geometry into a two-layer design.

### PCB 3D Rendering

<p align="center">
  <img src="PCB/PCB_3D_View.png"
       alt="Three-dimensional antenna PCB rendering"
       width="700">
</p>

**Figure 4.** Altium Designer 3D rendering of the
antenna PCB prior to fabrication.

---


### Project Status

- Analytical antenna design: **Completed**
- Ansys HFSS modeling and optimization: **Completed**
- Altium Designer PCB layout: **Completed**
- PCB fabrication: **Pending**
- Physical antenna measurements: **Pending**

**Note:** The performance results presented in this repository are from HFSS simulations. The antenna has not yet been physically fabricated or characterized.

---

## 1. Project Objectives

- Design a rectangular microstrip patch antenna operating near 915 MHz.
- Calculate the initial antenna dimensions using analytical microstrip equations.
- Design a 50-ohm microstrip feed and investigate impedance-matching techniques.
- Model the antenna using Ansys HFSS.
- Optimize the resonant frequency and input reflection coefficient.
- Transfer the optimized antenna dimensions into a two-layer PCB layout.
- Prepare the design for eventual fabrication and VNA testing.
- Develop a foundation for future wireless communication experiments.

---

## 2. Antenna Design Theory

A rectangular microstrip patch antenna consists of a conductive radiating patch separated from a ground plane by a dielectric substrate.

The patch supports a resonant electromagnetic field distribution, with the fundamental mode occurring when the resonant dimension is approximately one-half of the guided wavelength.

Because some of the electromagnetic field exists in the surrounding air, the antenna's effective dielectric constant differs from the relative permittivity of the substrate itself.

### Initial Patch Width

The initial patch width was calculated using:

$$
W=\frac{c}{2f_0}\sqrt{\frac{2}{\varepsilon_r+1}}
$$

Where:

- $W$ = Patch width
- $c$ = Speed of light
- $f_0$ = Target resonant frequency
- $\varepsilon_r$ = Relative dielectric constant

### Effective Dielectric Constant

To account for the fringing electromagnetic fields around the microstrip structure, the effective dielectric constant was estimated as:

$$
\varepsilon_{eff}=
\frac{\varepsilon_r+1}{2}
+
\frac{\varepsilon_r-1}{2}
\left(1+\frac{12h}{W}\right)^{-1/2}
$$

Where $h$ is the substrate dielectric thickness.

### Fringing Field Extension

Fringing fields make the resonant patch electrically longer than its physical length.

The approximate extension at each radiating edge is:

$$
\Delta L=
0.412h
\frac{(\varepsilon_{eff}+0.3)(W/h+0.264)}
{(\varepsilon_{eff}-0.258)(W/h+0.8)}
$$

### Patch Length

The effective patch length was determined using:

$$
L_{eff}=\frac{c}{2f_0\sqrt{\varepsilon_{eff}}}
$$

The physical patch length was then calculated as:

$$
L=L_{eff}-2\Delta L
$$

These equations provided the initial antenna geometry before electromagnetic optimization in HFSS.

### Analytical Design Results

Using a target resonant frequency of 915 MHz, substrate dielectric constant of 4.6, and dielectric thickness of 1.53 mm, the analytical calculations produced:

| Parameter | Calculated Value |
|---|---:|
| Design frequency | 915 MHz |
| Patch width | 97.90 mm |
| Patch length | 76.23 mm |
| Effective dielectric constant | 4.452 |
| Effective patch length | 77.64 mm |
| Fringing field extension | 0.708 mm |
| Estimated 50-ohm feed width | 2.85 mm |
| Initial inset depth | 21.63 mm |

These values served as the starting point for the full-wave electromagnetic simulation.

---

## 3. Substrate Selection

The antenna was designed around **Shengyi S1000H TG150**, an FR-4-family PCB laminate.

This material was selected to provide a relatively low-cost and accessible fabrication option while establishing defined dielectric properties for the simulation.

### Substrate Parameters

| Parameter | Value |
|---|---|
| Material | Shengyi S1000H TG150 |
| Relative permittivity | 4.6 |
| Loss tangent | 0.011 |
| Nominal board thickness | 1.6 mm |
| Modeled dielectric thickness | 1.53 mm |
| Copper thickness | Approximately 35 µm (1 oz) |
| PCB layers | 2 |

The dielectric properties were based on published values near 1 GHz.

Because actual substrate properties and fabricated layer thicknesses may differ from the modeled values, some resonant-frequency shift is expected during physical testing.

---

## 4. Inset-Fed Impedance Matching

One of the primary design challenges was matching the antenna input impedance to a standard **50-ohm RF feed line**.

A rectangular patch generally exhibits a relatively high input resistance near its radiating edge.

Several feeding methods were considered:

- Coaxial probe feeding
- Quarter-wave impedance transformer
- Inset microstrip feeding

### Why Inset Feeding?

An inset-fed structure was selected because it allows the patch and microstrip feed to be implemented on the same copper layer.

This simplifies PCB fabrication and provides a convenient way to adjust the input impedance.

Moving the feed point inward from the radiating edge changes the local input resistance.

The main matching parameters were:

- **Feed width:** Controls the characteristic impedance of the microstrip transmission line.
- **Inset depth:** Adjusts the feed-point resistance.
- **Inset gap:** Influences local coupling and the impedance match.

The initial feed geometry was calculated analytically and then refined in HFSS.

### Final Feed Geometry

| Parameter | Final Value |
|---|---:|
| Feed-line width | 2.77 mm |
| Inset depth | 25.45 mm |
| Inset gap | 1.39 mm |
| Target feed impedance | 50 ohms |

---

## 5. Ansys HFSS Electromagnetic Simulation

After completing the analytical design, the antenna geometry was implemented in **Ansys HFSS**.

The HFSS Antenna Toolkit was used to establish the initial rectangular inset-fed patch geometry.

A custom dielectric material was defined using the selected substrate properties.

The full-wave simulation accounts for effects that are not fully represented in the analytical equations, including:

- Finite substrate and ground-plane dimensions
- Electromagnetic fringing fields
- Dielectric losses
- Conductor geometry
- Feed discontinuities
- Electromagnetic radiation into the surrounding region

### Resonant Frequency Optimization

The initial valid HFSS simulation produced a resonance near:

**873.4 MHz, with S11 approximately -11.6 dB.**

This resonance was below the 915 MHz target.

Because the patch's resonant frequency depends strongly on its effective resonant length, the patch length was adjusted to move the resonance toward the target frequency.

The feed and inset geometry were also refined to improve the impedance match.

### Final HFSS Results

| Parameter | Final Result |
|---|---:|
| Target frequency | 915 MHz |
| Simulated resonant frequency | 919.6 MHz |
| Return loss (S11) | -16.92 dB |
| Resonant frequency deviation | +0.50% |
| Reflection coefficient magnitude | Approximately 0.143 |
| Reflected power at resonance | Approximately 2.0% |
| VSWR at resonance | Approximately 1.33:1 |

The simulated antenna resonated approximately **4.6 MHz above the target frequency**.

The final S11 value of **-16.92 dB** indicates a reasonably strong simulated impedance match at resonance.

The difference between the analytical prediction and the HFSS result illustrates the importance of refining idealized antenna equations using full-wave electromagnetic simulation.

---

## 6. Final Antenna Geometry

The final simulated dimensions were:

| Parameter | Analytical Design | Final HFSS Design |
|---|---:|---:|
| Patch length | 76.23 mm | 75.30 mm |
| Patch width | 97.90 mm | 98.00 mm |
| Feed width | 2.85 mm | 2.77 mm |
| Inset depth | 21.63 mm | 25.45 mm |
| Inset gap | Simulation-tuned | 1.39 mm |
| Dielectric thickness | 1.53 mm | 1.53 mm |
| Substrate length | Design-dependent | 234.4 mm |
| Substrate width | Design-dependent | 156.0 mm |

The antenna geometry was selected based on the final impedance-matching and resonant-frequency results.

---

## 7. PCB Design in Altium Designer

Following HFSS optimization, the antenna geometry was transferred into **Altium Designer** for PCB implementation.

The design uses a two-layer PCB structure consisting of:

- **Top copper layer:** Radiating patch and inset-fed microstrip transmission line
- **Bottom copper layer:** RF ground plane
- **Dielectric substrate:** Shengyi S1000H TG150

The PCB design was developed to preserve the optimized antenna dimensions while preparing the structure for eventual fabrication.

### PCB Design Considerations

Important factors included:

- Maintaining the patch dimensions from HFSS
- Preserving the calculated 50-ohm feed-line width
- Accurately positioning the inset feed
- Accounting for the substrate thickness and dielectric properties
- Considering the transition between the microstrip line and an RF connector
- Preparing copper and solder-mask geometry for fabrication

The PCB layout represents the next step toward transitioning the simulated antenna into a physical RF system.

**Current status:** The PCB layout has been completed in Altium Designer, but fabrication and experimental validation remain pending.

---

## 8. Engineering Results and Lessons Learned

This project demonstrated several important principles of RF and antenna design.

### Analytical Design vs. Electromagnetic Simulation

Analytical equations provide useful initial dimensions, but they cannot fully account for the electromagnetic behavior of a finite PCB antenna.

HFSS was necessary to refine the resonant frequency and impedance match.

### Resonant Frequency Tuning

The simulated resonant frequency was sensitive to patch length.

Adjusting the resonant dimension helped move the antenna from approximately 873.4 MHz to 919.6 MHz.

### Impedance Matching

The position and geometry of the inset feed significantly affected the input reflection coefficient.

Refining the feed dimensions improved the simulated match to approximately -16.92 dB.

### PCB Implementation

The project provided practical experience transferring a simulated RF structure into a PCB layout.

This required attention to physical dimensions, substrate assumptions, feed geometry, and manufacturability.

---

## 9. Engineering Skills Demonstrated

| Skill | Application |
|---|---|
| RF Engineering | Resonance, impedance matching, and antenna design |
| Antenna Theory | Rectangular patch resonance and fringing-field analysis |
| Electromagnetic Simulation | Ansys HFSS modeling and full-wave analysis |
| Microstrip Transmission Lines | 50-ohm feed design and inset matching |
| PCB Design | Two-layer RF layout in Altium Designer |
| Engineering Optimization | Iterative tuning of resonant frequency and feed geometry |
| Simulation Analysis | S11, VSWR, reflection coefficient, and frequency deviation |
| Technical Documentation | Analytical calculations, simulation results, and technical reporting |

---

## 10. Future Work

The next stage of this project is to fabricate the PCB and experimentally verify the antenna's RF performance.

### Planned Development

1. **PCB Fabrication**
   - Verify the final manufacturing stackup.
   - Review fabrication files and RF connector geometry.
   - Manufacture the two-layer antenna PCB.

2. **VNA Measurements**
   - Measure S11 using a NanoVNA or equivalent vector network analyzer.
   - Identify the measured resonant frequency.
   - Determine the -10 dB impedance bandwidth.
   - Compare experimental performance against the HFSS model.

3. **Wireless Communication Testing**
   - Fabricate or obtain a second antenna.
   - Establish a short-range wireless link.
   - Investigate the behavior of the antenna in a practical communication system.

4. **Digital Modulation**
   - Explore on-off keying (OOK), BPSK, and QPSK.
   - Investigate baseband signal generation and RF transmission.

5. **Advanced Antenna Development**
   - Explore alternative printed antenna geometries.
   - Apply the lessons learned to future antenna arrays and beamforming systems.

---

## Tools and Technologies

- Ansys HFSS
- Altium Designer
- Microstrip Antenna Theory
- RF Impedance Matching
- Electromagnetic Simulation
- PCB Design
- S-Parameter Analysis

---

## Author

**Josiah Germain**  
Electrical Engineering — University of Houston

[GitHub Profile](https://github.com/jgermain)
