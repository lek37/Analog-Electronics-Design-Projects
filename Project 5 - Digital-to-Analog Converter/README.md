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

_This circuit schematic was created by CircuiTikz designer and the generated script was copy and pasted to the 'main.tex' file - [Here](https://www.circuit2tikz.tf.fau.de/designer/) is the link of the tool I used to create research-level figure in the report_. 


### Circuit Operation

There are three voltage inputs: $v_1,v_2,v_3$ represents the binary input, HIGH and LOW. For a LOW logic input (binary 0), the input is represented as 0V DC input. For a HIGH logic input (binary 1), the input is represented as 5V DC input. Each digital input is applied at three inputs $v_1,v_2,v_3$ through a scaled resistor value of $R,2R,4R$, respectively. Thus, each input resistor branch also produce a scaled current to the summing node (input node to the inverting op-amp input). The input $v_1$ connected through resistor $R$ drives the most amount of current to the summing node, since, so it acts like a most significant bit (LSB) in the binary input. Conversely, the input $v_3$ through resistor of value $4R$ drives the least amount of current, and thus acts like a least significant bit (LSB) in the binary input.


The op-amp U1 with the feedback resistor $R/2$ keeps the inverting input (-) approximately 0V  through negative feedback. This resistor also control the internal gain of the first op-amp (will be proved quantitatively in the calculation). As discussed, idealized op-amp model does not draw any current into the inverting/non-inverting input, the current from the summing node flows through the feedback resistor, producing an converted analog voltage given the input voltage from $v_1,v_2,v_3$. Since there are 8 input combinations from the three inputs, there will be 8 corresponding voltage level at the output. [1]


Since the digital input combinations goes through the inverting input terminal (-), the output voltage will be inverted as well at analog-converted voltage $v_{DAC}$. That mean the positive-valued input at $v_1,v_2,v_3$ will produce a corresponding output at $v_{DAC}$ with a negative sign. To invert the voltage, a op-amp U2 is used as a **inverting voltage amplifier** with negative gain to revert the sign of $v_{DAC}$. 

### Calculation:

By assuming the operational amplifiers to be at ideal conditions and basic circuit analysis, here is the function of output analog voltage in terms of the digital input voltage (0 and 5V - represents logic LOW and logic HIGH). 

$$v_{out}=\frac{1}{2}v_1 + \frac{1}{4}v_2 + \frac{1}{8}v_3 $$

Thus, we can have the table represents the expected analog voltage based on the digital input. Note that for this table, a 0 - logic LOW would be 0V input, and a 1 - logic HIGH would be 5V input. 

 
| $v_1$ | $v_2$ | $v_3$ | $v_{out}$ |
| ----- | ----- | ----- | ------    |
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0.625 |
| 0 | 1 | 0 | 1.25 |
| 0 | 1 | 1 | 1.875 |
| 1 | 0 | 0 | 2.5 |
| 1 | 0 | 1 | 3.125 |
| 1 | 1 | 0 | 3.75 |
| 1 | 1 | 1 | 4.375 |

