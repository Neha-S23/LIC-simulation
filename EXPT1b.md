### 1.CIRCUIT DIAGRAM
![Screenshot 2025-02-17 210906](https://github.com/user-attachments/assets/d25d8ae8-dc37-4eaa-b3b9-41d962487f60)

 ### 2. COMPONENTS USED
 | Components | Value/Model | Purpose |
 |------------|-------------|---------|
 |MOSFET (M1) | CMOSN (TSMC 0.18um) | Main active element |
 | MOSFET (M2) | CMOSP (TSMC 0.18um) | Main active element (replacing resistor (R1) |
 | Voltage source (V1) | 1.8V | Supply voltage |
 | Voltage source (V2) | SINE(0.9 50m 1k) | AC input signal(1kHz, 50mV AC + 0.9V DC) |
 | MOSFET model library | .lib "Documents\LTspice\tsmc018.lib"| Defines MOSFET characteristics |   

  ### 3. SIMULATION PROCEDURE
 Now for the above circuit diagram, we are doing the analysis by replacing the resistor R1 with a PMOSFET and compare the result with the first circuit.
 ### <ins>3.1 DC operating point analysis</ins>
 - In this simulation , a DC supply volatge(VDD) of 1.8V is given and pMOSFET is used.
 - Here as the power rating is 100mW ,we have considered drain current(Id) as 55uA (from the equation P = VDD*I). Set the value for VB( gate voltage of PMOSFET) and change the length(L) and width(W) of both the MOSFET till we get the drain current as 55uA.The gate terminal of the MOSFET is biased at 0.9V DC, while the source terminal is grounded(0V). The drain volatge(Vd) is determined by the circuit components and the MOSFETS's characteristics. Since the threshold voltage (Vth) is 0.37V , the applied Vgs = 0.9V ensures that the MOSFET is turned ON.               
 
 After running the .op simulation , the DC volatges at key nodes are observed. 
 ![Screenshot 2025-02-17 203650](https://github.com/user-attachments/assets/6ca4766a-0536-4b50-a9ad-9c02e07ae9a3)

-  The MOSFET's drain current(Id) and the output volatge  are also obtained.
- Based on these values, we determine whether the MOSFET operates in Saturation(for amplification), Triode( for switching) or Cutoff( if OFF). If the drain volatge is significantly lower than VDD, the MOSFET is conducting and likely in saturation mode, which essential for amplification purposes.

 ### <ins>3.2 Transient response</ins> 
 An AC signal is apllied to the circuit using sine wave input volatge source parameters:   
 
 - Amplitude: 50mV(peak)
 - Frequency: 1kHz
 - DC offset: 0.9V
The simulation runs for 3 milliseconds(.trans 3m). The output waveform is observed at the drain of the MOSFET. If there's a phase shift than the circuit is functioning as an amplifier.
![Screenshot 2025-02-17 201455](https://github.com/user-attachments/assets/84125f1b-41f4-4398-8b09-b85c52b57692)

### <ins>3.3 AC analysis</ins>
An AC signal sweep is applied to the circuit over a wide range of frequencies, from 0.1 Hz to 1T Hz, using a logarithmic scale. The AC input is a small signal sine wave, and the gain is measured as the ratio of output peak voltage to input peak voltage in decibels. The simulation uses the following command:    
(.ac dec 10 0.1 1T)  

Here,
- dec 10: Takes 10 data points per decade for a smooth response curve.
- 0.1 Hz to 1T Hz: Defines the frequency sweep range.
![Screenshot 2025-02-17 201607](https://github.com/user-attachments/assets/6755d5eb-2a9a-4c18-bb1e-c7f7017064c9)

### 4. OBSERVATION
### <ins>4.1 DC operation point analysis</ins>    
- Gate Voltage(Vg): 0.9V
- Source Voltage(Vs): 0V
- Bias Voltage(Vb): 0.588
- Drain Voltage or Vout: 1.18V which is different from the expected output i.e 1.74445V as we have applied bias voltage to the gate terminal of the pMOSFET.
- Drain current: 55uA

### <ins>4.2 Transient analysis</ins>
- Input signal charcteristics: A 1kHz sine wave and 50mV peak amplitude and 0.9V DC offset was applied.
- Observed Output voltage(Vout): The output peak voltage was measured as 1.748V of the sine wave, indicating a successful amplification.
- Waveform integrity: The amplified signal retainsits shape without significant distortion, confirming proper circuit operation.

### <ins>4.3 AC analysis</ins>       
- Voltage Gain: The circuit shows a gain of 1.841dB. This indicates significant amplification of the input signal.
- Phase shift: At 1k Hz, the output waveform lags the input by approximately 120 degree, as calculated from the transient response graph. This suggests a frequency-dependent phase delay.

### 5. INFERENCE   
- DC operating point analysis cofirmed that the MOSFET operates in saturation region. The observed drain voltage (1.18V) and the drain current(55uA) align with theoretical values.
- Transient analysis verified that the circuit amplifies the input 1k Hz sine wave with minimal distortion. The output peak voltage of 1.372V suggests successful signal amplification. A phase shift in output indicates that the circuit introduces delay, which is typical in amplifiers.
- AC analysis showed a voltage gain of 14dB indicating strong signal amplification. There is a significant difference between the AC analysis gain(14dB) and transient analysis gain (28.767dB), which is mainly due to the phase shift, frequency-dependent behaviour, and how each analysis measures gain. The phase shift of ~120 degree at 1k Hz suggests that the frequency-dependent behaviour must be considered for applications requiring precise phase alignment.
 
### 6. CONCLUSION
- The CMOS circuit simulated in LTSpice functions as an amplifier, operating in the saturation region with stable gain, phase shift amd transient response.
-  The observed voltage gain and output characteristics validate its use in low-power amplification applications.
-  Further analysis, such as determining cutoff frequency and bandwidth, will help optimize the circuit for specific design requirements.


