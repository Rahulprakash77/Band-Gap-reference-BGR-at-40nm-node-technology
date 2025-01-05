# Band-Gap-reference-BGR-at-40nm-node-technology

The Bandgap Reference (BGR) circuit is a fundamental component in analog and mixed-signal IC design due to its ability to generate a stable and temperature-independent reference voltage. It is crucial for ensuring reliable performance in systems like ADCs, DACs, and power management circuits. Designing a BGR circuit provides insight into precision analog design, including temperature compensation and process variation handling. It is a versatile building block, widely used in VLSI and microelectronics, making it an essential skill for analog circuit designers.

## Introduction to BGR
The Bandgap Reference (BGR) is a circuit which gives a constantv DC output voltage also called as reference voltage which is independent of supply voltage variation and temperature variation.

![BGR1](https://github.com/user-attachments/assets/788178a0-a2d5-4cca-8de5-e9ee3aaae183)



### Why BGR 
- A battery is not suitable to use as a reference voltage source as it's voltage reduces with time
  
- A typical power supply gives noisy output or ripple superimposed in dc so it is also not suitable 
  
- An use of voltage reference IC with buried Zener diode, requires additional components and high frequency filtering circuits
  
- Unavaibility of low voltage zener diode

**Solution**
- Ease of integration of Bangap reference wthn bulk CMOS, Bi-CMOS or Bipolar technologies without the use of  external components makes it suitable to use it as refernce voltage generator.

### Features of BGR
- Reference voltage generation is independent of temperatue variation, Power supply variation and circuit loading
- Low Output voltage of 1.2v (close to the band gap energy of silicon at 0 deg kelvin)
- It finds applications in analog, digital, mixed mode, RF and system-on-chip (SoC).

### Applications of BGR
- Low dropout regulators (LDO)
- DC-to-DC buck converters
- Analog-to-Digital Converter (ADC)
- Digital-to-Analog Converter (DAC)



## 2. BGR Introduction

### 2.1 BGR Principle
The working principle of BGR circuits is to add a voltage with negative temprature coefficient to another voltagw with positive temperature coefficient. Generally semiconductor diode gives a voltage with negative temp coefficient and behave as CTAT. A PTAT circuit exactly works opposite to that of CTAT giving positive temp coefficient. So when these two voltages are added gives a constant voltage reference with respect to temp.

![BGR_Principle](https://github.com/user-attachments/assets/0cf802bf-04df-437a-b7f0-75ecd2fdf128)


#### 2.1.1 CTAT Voltage Generation
Usually semiconductor diodes provides -ve temco of voltage with value -2mV/deg Centigarde. i.e. CTAT behaviour.  
## 2. BGR Introduction

### 2.1 BGR Principle
The working principle of BGR circuits is to add a voltage with negative temprature coefficient to another voltagw with positive temperature coefficient. Generally semiconductor diode gives a voltage with negative temp coefficient and behave as CTAT. A PTAT circuit exactly works opposite to that of CTAT giving positive temp coefficient. So when these two voltages are added gives a constant voltage reference with respect to temp.

![CTAT](https://github.com/user-attachments/assets/7e87b5eb-1b21-4dda-9c65-5e037ab7db29)


#### 2.1.1 CTAT Voltage Generation
Usually semiconductor diodes provides -ve temco of voltage with value -2mV/deg Centigarde. i.e. CTAT behaviour.  

![CTAT](https://github.com/user-attachments/assets/a1f827cd-1f8d-4e2b-bd2d-7d6fa688bbd7)


#### 2.1.2 PTAT Voltage Generation

![Equation](https://github.com/user-attachments/assets/cbdb3328-3290-494e-ab9a-79355890d464)


So to get a PTAT Voltage generation circuit we have to separate VT from Is. It can be obtained as shown below

![PTATCKT](https://github.com/user-attachments/assets/b3ef414f-f20d-4b86-9258-eedf3b11c434)


In the above circuit same amount of current I is flowing in both the branches. So the node voltage A and B are going to be same V. Now in the B branch if we substract V1 from V, we get Vt independent of Is.

![PTATEQN](https://github.com/user-attachments/assets/4ff72839-edcc-43d0-8567-1fd02d4fcd72)


From above we can see that the voltage V-V1 is PTAT in nature with very less slope as compared to the CTAT. In order to cancel the opposite slope magnitude of slope must be equal. So diode connected multiple BJTs are used resulting in small current with each dipode and hence results into ith eincrese in slope of V-V1.

![PTAT](https://github.com/user-attachments/assets/b6d73507-2b72-454c-bd64-d24539ea6b20)


### 2.2 Types of BGR
Based on Architecture there are two types

- Using Self-biased current mirror  
- Using Operational-amplifier 

Based  on Application BGR can be classified as
- Low-voltage BGR
- Low-power BGR
- High-PSRR and low-noise BGR
- Curvature compensated BGR

We are going to design our BGR circuit using Self-biased current mirror architecture.

### 2.3 Self-biased current mirror based BGR

The Self-biased current mirror based BGR consists of following components.

- CTAT voltage generation circuit
- PTAT voltage generation circuit
- Self-biased current mirror circuit
- Reference branch circuit
- Start-up circuit

#### 2.3.1 CTAT Voltage generation circuit
The CTAT Voltage generation circuit consist of a diode connected BJT which gives CTAT nature as discussed above.


![CTAT1](https://github.com/user-attachments/assets/7bb8741c-e7be-43d7-8a15-274780121a56)


#### 2.3.2 PTAT Voltage generation circuit
The PTAT Voltgae generation circuit consist of multiple i.e. **N** BJTs diode connected with a series resistance. 

![PTAT1](https://github.com/user-attachments/assets/c552dbba-9597-4d26-a5c6-0edf264d42b6)


#### 2.3.3 Self-Biased Current Mirror Circuit
This doesn't need any external biasing circuit. It biases itself so called as Self biased ckt. 

![currentmirror](https://github.com/user-attachments/assets/d20f79d2-448e-4237-b4c7-a541bf64db33)


#### 2.3.4 Reference Branch Circuit
The reference circuit branch adds CTAT and PTAT volages and gives the final reference voltage which is constant. 

![refbranch1](https://github.com/user-attachments/assets/d204d980-5bbb-400f-9c2f-b240cec088ae)


#### 2.3.5 Start-up circuit
The start-up circuit is acting as a trigger to the self biased current mirror. It helps the transition from degenerative bias point (zero current) to the desired operation point i.e. desired current value mode. 

![startup](https://github.com/user-attachments/assets/2e44abbb-337f-42d7-9253-13a5ce604cad)


#### 2.3.6 Complete BGR Circuit
All the above components are connected together finally to get the complete BGR circuit.

![fullbgr](https://github.com/user-attachments/assets/b4a0544e-8fed-4f44-8b0e-f29a5d7d7279)

## BGR using current mirror circuit ( 40nm node technology ) 
### BGR Circuit and their connections in cadence virtuoso tool

![BGR_full Circuit](https://github.com/user-attachments/assets/65bbb844-7533-4d47-956e-9bfd067967dc)


## Vref output 
Vref plot with temp range -40 to 140 C , I got the only 0.5% variation in Vref

![vref_output](https://github.com/user-attachments/assets/ef3564ff-2535-4135-9523-1ba1b132c136)


