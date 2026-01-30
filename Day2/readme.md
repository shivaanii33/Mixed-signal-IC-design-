
# Day-2 

This document consists the continuation of Day one which includes 
- basic mosfet circuit analysis followed by analysis of the differential mosfet pair with differential input and single output  
- symbol creation and analysis using the cadence tool 
---

## **Circuit 1**

As analysed in the previous circuit (day-1), the resistor which is present in the circuit is replaced by the pmos in this circuit 

The  behaviour of the mosfet is analysed with pmos as the diode connected transistor in which drain and the gate terminals are conencted.


![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20203720.png)

### Parameters 
- Input -> 50mVp-p , 1KHz, Vdc = 0.6V 
- Supply VDD = 1V 
- Q1, Q2 -> w = 120nm , l = 45nm (deafult).

for the circuit to behave as the amplifier both the mosfets should be operation in the saturation region.

## 1) DC Analysis 

### Results

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20203752.png)

now the pmos behaves as the idea current source with the resistance as 1/gm 

- If nmos is Q1 and pmos is Q2 then the overall gain of the circuit will be -gm1/gm2 
- From the result the output voltage is obtained as 0.405V 

For the maximum output swing the Vout is expected to be nearly Vdd/2 ~ 0.5V 
- Hence this can be achieved by performing the parametric dc analsyis with varying the width of the pmos transistor from 120nm to 2um with 5 ans the step size  and observing the vout for the different values of Vdc (input biasing voltage)
- Thereby the proper values for the  width of pmos and Vdc can be obtained which is responsible for the maximum swing of the output 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20203812.png)

- for w= 1um (pmos) and Vdc = 0.5V the value of Vout will be equal to 0.5V (Vdd/2)

## 2) Transient Analysis 
### Results 
- The above mentioned values are fixed and transient analysis is carried out to get the proper amplification 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20210608.png)

## 3) AC Analysis 
![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20210629.png)

The gain of 0.68 is obtained from the circuit 

## **Circuit 2**

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20220739.png)

- From the previous circuit where the drain and the gate terminals of the pmos transistor were connected because of which it was behaving as the Diode connected transistor, 
- In this circuit the gate terminal of the pmos is biased with dc voltage 0.5V ensuring that pmos remains in the saturation region 
### Parameters 
- Pmos-> w = 1um; l = 45nm ; Vb1 = 0.5V 
remaning all follows the same as previos one with Vdc = 0.6V 

**The comparision between the Circuit 1 and 2 with both Transient and the frequency analysis can we observed with the below results**

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20220714.png)


![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20220727.png)


From this higher gain and there by the amplification can be observed from the circuit 2 because here the pmos is acting as the current source 


## **Circuit 3**

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20220943.png)

Differential mos amplifier with 2 pmos and 3 nmos 

### Parameters 
- pmos -> w=1um; l = 45nm.
- nmos -> w=120nm; l = 45nm.
- supply = vdd = 2V
- for the lower nmos fingers = 10
- input dc voltage = 1.2V , 
in order to verify the amplification Vin of one nmos is made 50mVp-p with 1KHz and 1V as ac amplitude and another n mosfet with 0vp-p and 0ac amplitude and only with the dc volatge 

**Results**

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20221041.png)

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20221131.png)

---

Once the circuit is ready for the purpose of layout design and fabrication the symbol creation is necessary 
- In which firstly, all the external sources are removed and they are labelled with the pins, save it.
- Create cell view-> from cellview-> octokatherine
- For the symbol you want rearrange the pins as required also adjust the boundary using the shaping tools, check it and save it 
- Open another cellview import the symbol you created from your library, this is the test circuit, now connect all the external sources and verify the results 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/75b1110d3817f1361fa0019cad4f1b00854bfe40/Day2/Images/Screenshot%202026-01-29%20221246.png)
 The results should be same as you got from your design. 

 ---
 Spectrum of the circuit using the rectangular window is also obtained 


 ![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/ca9e14aa5f81b7968232039ef6dfa53b15ef4320/Day2/Images/Screenshot%20from%202026-01-29%2010-34-47.png)


 ![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/ca9e14aa5f81b7968232039ef6dfa53b15ef4320/Day2/Images/Screenshot%20from%202026-01-29%2010-37-15.png)


- Now if the Vinp input voltage is made as 500mV the output will be clipped off 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/ca9e14aa5f81b7968232039ef6dfa53b15ef4320/Day2/Images/Screenshot%20from%202026-01-29%2010-36-08.png)

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/ca9e14aa5f81b7968232039ef6dfa53b15ef4320/Day2/Images/Screenshot%20from%202026-01-29%2010-36-59.png)























- [@octokatherine](https://www.github.com/octokatherine)

