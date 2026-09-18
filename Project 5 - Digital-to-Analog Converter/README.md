# 3-bit Resistor Weighted Digital-to-Analog Converter

## Overview:

For this project, the implementation of a 3-bit digital-to-analog converter will be carried out
with a full scale analog output voltage of 5V. The design utilized the functionality of an inverting
operational amplifier (op-amp), and using binary-weighted input resistors to convert a 3-bit digital
input as voltage into a corresponding analog output voltage. The whole project consists of three
main parts: theoretical explanation of how the process of digital-to-analog conversion operates, the
experimental result along with quantitative analysis of error that arises. Finally, a short discussion
on how the error arises and an alternative design will also be carried out as well.

## Design 

### Circuit Diagram

This is the circuit schematics of the DAC process used in this project:

<img width="726" height="241" alt="image" src="https://github.com/user-attachments/assets/742c7bfa-0459-40b0-8239-6d2df6c0cda8" />

_This circuit schematic was created by CircuiTikz designer and the generated script was copy and pasted to the 'main.tex' file - [Here](https://www.circuit2tikz.tf.fau.de/designer/) is the link of the tool I used to create research-level figure in the report (ignore the security message)_.


### Circuit Operation

There are three voltage inputs: $v_1,v_2,v_3$ represents the binary input, HIGH and LOW. For a LOW logic input (binary 0), the input is represented as 0V DC input. For a HIGH logic input (binary 1), the input is represented as 5V DC input. Each digital input is applied at three inputs $v_1,v_2,v_3$ through a scaled resistor value of $R,2R,4R$, respectively. Thus, each input resistor branch also produce a scaled current to the summing node (input node to the inverting op-amp input). The input $v_1$ connected through resistor $R$ drives the most amount of current to the summing node, since, so it acts like a most significant bit (LSB) in the binary input. Conversely, the input $v_3$ through resistor of value $4R$ drives the least amount of current, and thus acts like a least significant bit (LSB) in the binary input.


The op-amp U1 with the feedback resistor $R/2$ keeps the inverting input (-) approximately 0V  through negative feedback. This resistor also control the internal gain of the first op-amp (will be proved quantitatively in the calculation). As discussed, idealized op-amp model does not draw any current into the inverting/non-inverting input, the current from the summing node flows through the feedback resistor, producing an converted analog voltage given the input voltage from $v_1,v_2,v_3$. Since there are 8 input combinations from the three inputs, there will be 8 corresponding voltage level at the output. [1]


Since the digital input combinations goes through the inverting input terminal (-), the output voltage will be inverted as well at analog-converted voltage $v_{DAC}$. That mean the positive-valued input at $v_1,v_2,v_3$ will produce a corresponding output at $v_{DAC}$ with a negative sign. To invert the voltage, a op-amp U2 is used as a **inverting voltage amplifier** with negative gain to revert the sign of $v_{DAC}$. 

### Calculation:

By assuming the operational amplifiers to be at ideal conditions and basic circuit analysis, here is the function of output analog voltage in terms of the digital input voltage (0 and 5V - represents logic LOW and logic HIGH). 

$$v_{out}=\frac{1}{2}v_1 + \frac{1}{4}v_2 + \frac{1}{8}v_3 $$

Thus, we can have the table represents the expected analog voltage based on the digital input. Note that for this table, a 0 - logic LOW would be 0V input, and a 1 - logic HIGH would be 5V input. 

 
| $v_1$ | $v_2$ | $v_3$ | Decimal input |$v_{out}$ (V)|
| ----- | ----- | ----- | -----         | ------    |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0.625 |
| 0 | 1 | 0 | 2 | 1.25 |
| 0 | 1 | 1 | 3 | 1.875 |
| 1 | 0 | 0 | 4 | 2.5 |
| 1 | 0 | 1 | 5 | 3.125 |
| 1 | 1 | 0 | 6 | 3.75 |
| 1 | 1 | 1 | 7 | 4.375 |

## Measurement & Analysis

### Physical circuit on breadboard:

<img width="556" height="417" alt="image" src="https://github.com/user-attachments/assets/c250a478-e46e-4190-a1e6-a80ce3f53bd1" />ns

### Digital Input Generations:
I configured the Supplies channel of the AD3 as following:
- **Positive Supply (V+):** 5V. This is connected from the V+ probe of the AD3 to the common positive rail of the breadboard, to the V+ pin of the LM662CN op-amps.
- **Negative Supply**: -5V. This is connected straight from the V- probe of the AD3 to the V- pin of the LM662CN op-amps.

Additionally, the GND probe from the AD3 is connected to the negative rail of the breadboard. The digital input $v_1,v_2,v_3$ are placed at the positive rail (5V) or the negative rail (0V) correspond to logic HIGH (1) or logic LOW (0), respectively, to generate a 3-bit binary input combination. 

### Transfer Characteristics:
The table below shows the transfer characteristics of the DAC system:

| $v_1$ | $v_2$ | $v_3$ | Decimal input | $v_{theoretical}$ (V)| $v_{actual}$ (V) |
| ----- | ----- | ----- | -----         | ------    | ----- |
| 0 | 0 | 0 | 0 | 0 | 0.036 | 
| 0 | 0 | 1 | 1 | 0.625 | 0.653 |
| 0 | 1 | 0 | 2 | 1.25 | 1.236 | 
| 0 | 1 | 1 | 3 | 1.875 | 1.873 | 
| 1 | 0 | 0 | 4 | 2.5 | 2.484 | 
| 1 | 0 | 1 | 5 | 3.125 | 3.121 | 
| 1 | 1 | 0 | 6 | 3.75 | 3.733 | 
| 1 | 1 | 1 | 7 | 4.375 | 4.345 |

### Error Identification & Measurement:
**Gain error**: this quantity represents the percentage error of the actual full-scaled voltage versus the expected full-scaled voltage. For this project, $V_{FS,theoretical}=4.375V$, and $V_{FS,actual}=V_{out,111}-V_{out,000}=4.345V-0.036V=4.309V$

