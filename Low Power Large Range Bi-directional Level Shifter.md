# Low Power Large Range Bi-directional Level Shifter
##### Design_Name : Low_Power_Bi-directional_LRLS
##### Technology_Node : CMOS_28nm
##### Author : K Aruna Kumara Sarma
##### Company : HCL Technologies, Bengaluru. K.A
##### Event : IITH/SNPS/VSD analog hackathon

## Design Implementation & Simulation

### Table of Contents

- [Introduction](https://github.com/sarmakolavasi/LR_Bidirectional_LS/blob/main/Low%20Power%20Large%20Range%20Bi-directional%20Level%20Shifter.md#Introduction)
- [Technological Study Of Models](https://github.com/sarmakolavasi/LR_Bidirectional_LS/blob/main/Low%20Power%20Large%20Range%20Bi-directional%20Level%20Shifter.md#Technological-Study-Of-Models)
- [Circuit Design Implementation](https://github.com/sarmakolavasi/LR_Bidirectional_LS/blob/main/Low%20Power%20Large%20Range%20Bi-directional%20Level%20Shifter.md#Circuit-Design-Implementation)
- [VDDL2VDDH Simulation Waveform](https://github.com/sarmakolavasi/LR_Bidirectional_LS/blob/main/Low%20Power%20Large%20Range%20Bi-directional%20Level%20Shifter.md#VDDL2VDDH-Simulation-Waveform)
- [VDDH2VDDL Simulation Waveform](https://github.com/sarmakolavasi/LR_Bidirectional_LS/blob/main/Low%20Power%20Large%20Range%20Bi-directional%20Level%20Shifter.md#VDDH2VDDL-Simulation-Waveform)
- [Results And Performance](https://github.com/sarmakolavasi/LR_Bidirectional_LS/blob/main/Low%20Power%20Large%20Range%20Bi-directional%20Level%20Shifter.md#Results-And-Performance)
- [Conclusion](https://github.com/sarmakolavasi/LR_Bidirectional_LS/blob/main/Low%20Power%20Large%20Range%20Bi-directional%20Level%20Shifter.md#conclusion)
- [Author](https://github.com/sarmakolavasi/LR_Bidirectional_LS/blob/main/Low%20Power%20Large%20Range%20Bi-directional%20Level%20Shifter.md#author) 
- [Acknowledgements](https://github.com/sarmakolavasi/LR_Bidirectional_LS/blob/main/Low%20Power%20Large%20Range%20Bi-directional%20Level%20Shifter.md#acknowledgements)
- [References](https://github.com/sarmakolavasi/LR_Bidirectional_LS/blob/main/Low%20Power%20Large%20Range%20Bi-directional%20Level%20Shifter.md#references)

### Introduction

The sudden increase in demand for IOT & AI applications built up a craze for Low power & High performance modern designs in the SoC design community. Though level shifters were being used in order to cater the controductory requirements but the techniques were ineffectual, as a part of the power saved by multi level voltage islands is lost due to inherent power consumption characteristic attributes of inefficient level shifter cells leads to energy consumption by itself.

The proposed "Low-power architecture for a Bi-derectional level shifter" design has been created on Synopsis [Custom Compiler](https://www.synopsys.com/implementation-and-signoff/custom-design-platform/custom-compiler.html) software and simulated using [PrimeWave](https://www.synopsys.com/implementation-and-signoff/ams-simulation/primewave.html) environment. 

<p align="center">
<img src="https://user-images.githubusercontent.com/100507370/155894698-4e5a2d8e-1e2c-4e5d-a2f6-96a631cddc69.png">
</p>
<p align="center">
Fig 1. Transistor level schematic of proposed bi-directional level shifter.
</p>

Fig 1. shows the Transistor level bi-directional level shifter schematic, This proposed circuit will resolve the observed huge short circuit or direct path current exists from VDDH to VSS which occurs in many of the back to back connected bi-directional level shifters.

### Technological Study Of Models

Before the design of any circuit, a thorough understanding of the characteristics of used devices is required. This becomes even more crucial for MOS devices of lower technology nodes which deviate a lot from the ideal MOS characteristics due to second order effects.

The device models characterization of NMOS and PMOS was performed using standard circuits as part of model study. The mosfets were taken from SAED_32_28 PDK library with width to length ratio of 0.3um/0.03um. The drain to source voltages and gate to source voltages were sweeped to produce the below plots.

<br/>
<p align="center">
<img src="https://user-images.githubusercontent.com/41693726/155748353-a8f99600-4016-4db4-a576-994fc59fc3b5.png">
</p>
<p align="center">
Fig 2. I_D vs V_DS for NMOS device.
</p>

Fig 2. presents the drain current (I_D) of NMOS device as a function of drain to source voltage (V_DS) for some fixed value of gate to source voltage (V_GS). As can be observed the device in saturation region has a high slope indicating a strong dependence on V_DS. This presents a challenge to the circuit designer as the MOS no longer remains an ideal transconductance device.

<br/>
<p align="center">
<img src="https://user-images.githubusercontent.com/41693726/155748383-1163c4ea-103f-49d2-a4af-e50f61ac9591.png">
</p>
<p align="center">
Fig 3. I_D vs V_GS for NMOS device.
</p>

Fig 3. presents I_D of NMOS device as a function of V_GS for some fixed value of V_DS. As can be observed the device is no longer follows the square law but has a linear rise even in saturation region due to velocity saturation effects.

<br/>
<p align="center">
<img src="https://user-images.githubusercontent.com/41693726/155748683-c204c584-82d0-460f-80d6-8104c5c9ba94.png">
</p>
<p align="center">
Fig 4. I_D vs V_SG for PMOS device.
</p>

Fig 4. presents I_D of PMOS device as a function of V_SG for some fixed value of V_SG. The PMOS device has lower current than NMOS for similar voltage levels.

### Circuit Design Implementation

<p align="center">
<img src="https://user-images.githubusercontent.com/100507370/155895536-d4966685-7eb3-4291-9211-ec547f3fe16c.png">
</p>
<p align="center">
Fig 5a. Low Power Large Range Bi-directional Level Shifter
</p>

#### Design Netlist

<p align="left">
<img src="https://user-images.githubusercontent.com/100507370/156118123-337a177a-f942-46f1-ac9b-f06884c2947e.PNG">
</p>
<p align="center">
Fig 5b. Circuit Netlist Of Low Power Large Range Bi-directional Level Shifter
</p>

Fig 5b. Shows Low Power Large Range Bi-directional Level Shifter Schematic can perform below operations

The Fig 5a, Shows Low Power Large Range Bi-directional Level Shifter Schematic can perform below operations
#### Operation: 1  IN to OUT, VDDL to VDDH (EN = 0).
- The port IN is associated with voltage level VDDL while port OUT is with VDDH.
- During to VDDL to VDDH operation the EN signal is to be set as low (EN = 0).
- The INB is generated from the port IN and is connected to M12, M13 and M17.
- For M12 and M13 the supply is connected to voltage level VDDL via M9, thus driving gate of M16 with logic level of VDDL.
- The supply for the cross coupled level shifter also connected to high voltage level VDDH via M10.
- If IN = 0 then, M16 is turned on and a logic low corresponding to VDDH is driven by M16 to the port OUT.
- If IN = 1 then, M17 is turned on and a logic high corresponding to VDDH is driven M14 to the port OUT

##### VDDL2VDDH Simulation Waveform

<p align="center">
<img src="https://user-images.githubusercontent.com/100507370/156117513-97ba9863-22f1-4977-8cc1-5de2e39445f2.PNG">
</p>
<p align="center">
Fig 6. Bi-directional Level Shifter "VDDL2VDDH" Simulation Input And Output Waveforms
</p>

The bi-directional level shifter circuit simulation performed and the fig 6. shows the input & output of "VDDL2VDDH" waveform obtained 600mv level up shift after proper sizing of the devices accoding to the available models in CMOS 28nm PDK.

#### Operation: 2  IN to OUT, VDDH to VDDL (EN = 1).
- The port IN is associated with voltage level VDDH while port OUT is with VDDL.
- During to VDDH to VDDL operation the EN signal is to be set as high (EN = 1).
- The INB is generated from the port IN and is connected to M12, M13 and M17.
- For M12 and M13 the supply is connected to voltage level VDDH via M8, thus driving gate of M16 with logic level of VDDH.
- The supply for the cross coupled level shifter also connected to low voltage level VDDL via M11.
- If IN = 0 then, M16 is turned on and a logic low corresponding to VDDL is driven by M16 to the port OUT.
- If IN = 1 then, M17 is turned on and a logic high corresponding to VDDL is driven M14 to the port OUT

##### VDDH2VDDL Simulation Waveform

<p align="center">
<img src="https://user-images.githubusercontent.com/100507370/156117629-f3f76e59-54c4-477d-9d3b-183449096d4d.PNG">
</p>
<p align="center">
Fig 7. Bi-directional Level Shifter "VDDH2VDDL" Simulation Input And Output Waveforms
</p>

The bi-directional level shifter circuit simulation performed and the fig 7. shows the input & output of "VDDH2VDDL" waveform obtained 600mv level down shift after proper sizing of the devices accoding to the available models in CMOS 28nm PDK.

### Results And Performance

<p align="center">
<img src="https://user-images.githubusercontent.com/100507370/156139784-63374734-cbe4-4631-9c9f-82eee7f1de86.PNG">
</p>
<p align="center">
Fig 8. Bi-directional Level Shifter Simulation Results
</p>

The table presents results and performance of the circuit that previously done in the literature. Still a clear trade off can be acheived with further re-search and development with advanced technology nodes.

### Conclusion

The repository presents the design and simulation of the proposed "Low-power Large Range Bi-directional Level Shifter", the design architecture has been imple  mented using CMOS 28nm PDK, created on Synopsis [Custom Compiler](https://www.synopsys.com/implementation-and-signoff/custom-design-platform/custom-compiler.html) software and simulated using [PrimeWave](https://www.synopsys.com/implementation-and-signoff/ams-simulation/primewave.html) environment.

The design supports full rail large range level shift of 600mv on CMOS 28nm technology node. The design supports lower leakage at 1.8V headers and provides proper level shift in both directions. Future works can include improvement of design using better design schemes and biasing techniques to make lower area efficiant and to meet PPA requirements. 

### Author

Aruna Kumara Sarma K, Masters in (VLSI & Embedded Systems Design), HCL Technologies Bengaluru, K.A.

### Acknowledgements

- [Synopsys](synopsys.com/company/contact-synopsys/office-locations/india/about-synopsys-india.html)
- [IIT Hyderabad](https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/)
- [Chinmay Panda, Technical Officer, IIT Hyderabad](https://ee.iith.ac.in/staff.html)
- [Kunal Ghosh, Co-founder, VSD Corp. Pvt Ltd.](https://www.linkedin.com/in/kunal-ghosh-vlsisystemdesign-com-28084836?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_contact_details%3B0xcWjpLDThSEo6S9UPO9Tw%3D%3D)
- [Active and vibrant hackathon community](https://hackathoniith.in/)

### References

1. Digital Integrated Circuits: A Design Perspective (Printice Hall Electronics and Vlsi Series)
   by Jan Rabaey (Author), Anantha Chandrakasan (Author), Borivoje Nikolic (Author).
2. Design of Analog CMOS Integrated Circuits (Behzad Razavi), McGraw-Hill, 2001.
3. [Design & Reuse](https://www.design-reuse.com)
4. [CiteSeerX](https://citeseerx.ist.psu.edu)
