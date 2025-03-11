# LINEAR INTEGRATED CIRCUITS
## EXPERIMENT 3:- DIFFERENTIAL AMPLIFIER
### INTRODUCTION:
- Differential amplifier is an elementary circuit used in analog electronics to amplify the difference between two input signals with rejection of common-mode signals.
- It is a common circuit element in operational amplifiers (op-amps), analog signal processing, and communication circuits.
![Screenshot 2025-03-09 221750](https://github.com/user-attachments/assets/04c26893-194f-4701-9e92-885c8e603a16)
 This is an ample circuit to explain the MOS Differential Amplifier.
- The Circuit consists of 2 transistors Q1 and Q2 which are the input pair.
- Rd resistors are used to convert the drain currents to output currents.
- VDD and VSS act as input and output points. The Total current flowing in VSS is the sum of the current in both branches.
-  When the differential inputs are equal, the current flowing in the branches is equal.
- When given the same inputs to the gate terminal of both the branches, it is called COMMON MODE Amplifier which has high noise interference rejection.

### DESIGN QUESTION
Vdd=2V Vin,cm=1V Vo,cm=1.1V Vp=0.4V P<=1mW 

### CASE-1: Circuit with Rss resistor
![Screenshot 2025-03-09 222853](https://github.com/user-attachments/assets/0232c172-c0aa-47b8-ac0e-1996f3ec84f0)

DC ANALYSIS
![Screenshot 2025-03-04 100606](https://github.com/user-attachments/assets/f988e970-0d8c-490f-8d4e-6ffc4d48b290)
MOSFET dimensions: w=19.36um l=180nm

TRANSIENT ANALYSIS
![Screenshot 2025-03-04 102916](https://github.com/user-attachments/assets/648ecb29-fbc0-4bb7-916f-885709e8fe13)
- Gain Av=-7.488 V/V
- Gain in dB = 17.48dB
![Screenshot 2025-03-04 110250](https://github.com/user-attachments/assets/d58d2307-022c-4a33-a1ec-71dc0d45e8b8)

AC ANALYSIS
![Screenshot 2025-03-04 111741](https://github.com/user-attachments/assets/7ae90ef5-7b63-48bb-b41a-79edf5b500ad)
The above figure shows the 3dB frequency of the circuit.

### CASE-2 Circuit with current source 
![Screenshot 2025-03-09 224155](https://github.com/user-attachments/assets/f1a243af-daa5-4169-96b6-565ea5f6f0b1)

DC ANALYSIS
![Screenshot 2025-03-09 224841](https://github.com/user-attachments/assets/06dd5648-b291-4b14-9505-8a5333c55468)
MOSFET dimensions: w=19.3821um l=180nm

TRANSIENT ANALYSIS
![Screenshot 2025-03-09 225329](https://github.com/user-attachments/assets/0893f364-cc77-4808-b62e-aeb070c34783)
- The gain of the circuit Av=-4.701 V/V.
- There is 180 degree phase shift in the output graph.
- The gain is lower compared to the gain we got from the previous circuit where we used a resistor.
- This can be due to CMRR which affects the gain of circuit.

AC ANALYSIS
![001](https://github.com/user-attachments/assets/4f959117-24c5-4f5b-aa9d-6f72eff25fad)

The 3dB frequency of the circuit.

### CASE-3 Circuit with N-MOS
![Screenshot 2025-03-11 233451](https://github.com/user-attachments/assets/6044ed89-f8e1-4601-be53-b409df67027a)

DC ANALYSIS
![Screenshot 2025-03-09 213008](https://github.com/user-attachments/assets/ec659da4-d19a-40d9-b11c-0400e06382fd)

TRANSIENT ANALYSIS
![Screenshot 2025-03-09 213206](https://github.com/user-attachments/assets/89c261a0-943e-4f2f-aa43-ae95932e38b0)
The gain of the circuit Av= -4.862 V/V and there is a 180 degree phase shift. 

AC ANALYSIS
![Screenshot 2025-03-11 233907](https://github.com/user-attachments/assets/9e73ce03-6015-4c2f-bda5-9628fa4b51c8)

### INFERENCES
- The stability of each circuit increases with resistor circuit being least stable and the NMOS circuit being the most stable.
- Small variations in gain and bandwidth is also seen.
- Replacing both the Rd resistors with MOSFETS gives more stability to the circuit. This also increases the gain of the circuit.
- Mosfet based differential circuit is highly preferable to use in ICs since it has high CMRR, draws minimal power, high gain, high input impedance.
