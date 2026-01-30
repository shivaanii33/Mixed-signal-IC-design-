
# DAY-3

Third day of the continuos hands on session using the cadence tool, was very impactful in understanding and analysing the basic BGR circuit 

- followed by extracting the necessary parameters such as PTAT and CTAT 
- explored cadence mathemaetical calcualtor to obtain the derivative and also it is used to plot the necessary / required equations 
- hence verifying the bgr circuit by looking at the ref voltage at the output 

## Circuit 1 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/f62bc21ebfcd7feb2594a477437f89b5cd53574c/DAY-3/Images/Screenshot%202026-01-30%20234421.png)

**specifications**

- voltage supply VDD = 2V 
- 2 current source each of 100uA.
- 2 npn transistors with the ratio 1:100

Using this circuit DC analysis is carried out by sweeping the temperature variable from 0 to 100 degree celcius.

VOUT1 = VBE1 and VOUT2 = VBE2 is obtained from the dc analysis 

- CTAT refers to the complementary to the absolute temperature, we have VBE1 = CTAT which is varying inversly with the increasing temperature 
- While VBE1 - VBE2 = delta VBE >- is the PTAT refers to the proportional to the absolute temperature.
- To plot the equation for PTAT the calculator is used and here are the results :

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/f62bc21ebfcd7feb2594a477437f89b5cd53574c/DAY-3/Images/Screenshot%20from%202026-01-29%2011-09-59.png)

Now for the purpose of analysing and calculations, The derivatives of CTAT and PTAT is also obtained 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/f62bc21ebfcd7feb2594a477437f89b5cd53574c/DAY-3/Images/Screenshot%202026-01-30%20234337.png)


![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/f62bc21ebfcd7feb2594a477437f89b5cd53574c/DAY-3/Images/Screenshot%202026-01-30%20234405.png)

## Circuit 2 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/f62bc21ebfcd7feb2594a477437f89b5cd53574c/DAY-3/Images/Screenshot%20from%202026-01-29%2015-38-54.png)

The circuit is designed with the suitable values of resistors such that the whole idea of making the circuit independent of temperature is possible 
- this is carried out by the specific process 
- In this circuit CTAT which in the VBE1 is obatined through the dc analysis by varying the temperature 
- Where are PTAT is the difference between the points A AND B in the circuit which is again obtained using the calculator expresssion 
- Along side important criteria to ensure is that the output of the circuit is acting as the feedback loop and hence it is what driving the two transistors 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/f62bc21ebfcd7feb2594a477437f89b5cd53574c/DAY-3/Images/Screenshot%20from%202026-01-29%2015-38-05.png)


- the derivative of all three PTAT, CTAT AND vref(output) is plotted to verify how both CTAT and PTAT are nullifying the VREF and making is absolutely small 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/f62bc21ebfcd7feb2594a477437f89b5cd53574c/DAY-3/Images/Screenshot%202026-01-30%20234358.png)











