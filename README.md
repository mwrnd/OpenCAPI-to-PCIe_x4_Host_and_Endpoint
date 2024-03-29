**Work-In-Progress**: Design being tested.




# OpenCAPI to PCIe x4 Host and Endpoint

Designed to test simultaneous PCIe Host and Endpoint operation with the Innova-2.

![OpenCAPI to PCIe x4 Host and Endpoint Adapter](img/OpenCAPI_to_PCIe_x4_Host_Endpoint.jpg)

There are two [PCIE4](https://docs.xilinx.com/r/en-US/pg213-pcie4-ultrascale-plus/Introduction) blocks in the column of the Innova-2's OpenCAPI Quads.

![Innova-2 OpenCAPI Banks](img/Innova2_OpenCAPI_XCKU15P_FFVE1517_Banks.png)

The GTY Transceivers connected to the OpenCAPI Connector are in a column that does not contain the Configuration Block so it is impossible for the FPGA to be programmed within the [100ms PCIe power-up time limit](https://pcisig.com/specifications/ecr_ecn_process?speclib=100+ms). Motherboard boot must be delayed to allow the FPGA to configure itself before PCIe devices are enumerated. This can be accomplished by toggling the POWER button, then pressing and holding the RESET button for a second before releasing it. Or, [connect a capacitor across the reset pins of an ATX motherboard's Front Panel Header](https://github.com/mwrnd/ATX_Boot_Delay).

![Delay Boot Using Front Panel Header Capacitor](img/Delay_Boot_Using_FrontPanelHeader_Capacitor.jpg)

[OpenCAPI](https://files.openpower.foundation/s/xSQPe6ypoakKQdq/download/25Gbps-spec-20171108.pdf)-compatible SlimSAS 8x uses a **Host** version of the OpenCAPI **Carrier** pinout from the [ADM-PCIE-9V5 User Manual (Pg15-19of38)](https://www.alpha-data.com/xml/user_manuals/adm-pcie-9v5%20user%20manual_v1_4.pdf).




## Testing

![OpenCAPI to PCIe x4 Host and Endpoint in a System](img/OpenCAPI_to_PCIe_x4_Host_Endpoint_In-System.jpg)

```
TODO
```




### OpenCAPI I2C

The [innova2_xdma_opencapi](https://github.com/mwrnd/innova2_xdma_opencapi) project includes the ability to test I2C.

![Testing I2C using TC74](img/TC74_in_OpenCAPI-to-PCIe_x4.jpg)




## PCB Layout

All differential pairs are length-matched to within 1mm intra-pair (N-to-P) and each group of differential pairs (e.g., TX0-to-TX3) is similarly matched to within 1mm.

![OpenCAPI to PCIe Host and Endpoint PCB Layout](img/OpenCAPI_PCIe_x4_Host_and_Endpoint_PCB_Layout.png)




## Schematic

![OpenCAPI to PCIe Host and Endpoint Schematic](img/OpenCAPI_PCIe_x4_Host_and_Endpoint_Schematic.png)




## Bill Of Materials

| Designator(s) | Part Number             | Quantity | Value      | Footprint                           | Availability                                                                                               |
| ------------- | ----------------------- | -------- | ---------- | ----------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| U1            | SY75572LMG              |        1 |        N/A | QFN-16-1EP_3x3mm_P0.5mm             | [DigiKey](https://www.digikey.com/en/products/detail/microchip-technology/SY75572LMG-TR/5319585)           |
| U2            | DSC1124BI2-100-0000     |        1 |        N/A | OSC_SMD_IDT_JS6-6_5.0x3.2mm_P1.27mm | [DigiKey](https://www.digikey.com/en/products/detail/microchip-technology/DSC1124BI2-100-0000/5284202)     |
| J1            | U10A474240T             |        1 |        N/A | SlimSAS_8x_RA_U10-A474              | [DigiKey](https://www.digikey.com/en/products/detail/amphenol-cs-commercial-products/U10A474240T/17066204) |
| J2            | PPPC061LFBN-RC          |        1 |        N/A | PinHeader_1x06_P2.54mm_Vertical     | [DigiKey](https://www.digikey.com/en/products/detail/sullins-connector-solutions/PPPC061LFBN-RC/810178)    |
| J4            | 2-2387405-2             |        1 |        N/A | PCIe x4 Straddle Mount w/ Open End  | [DigiKey](https://www.digikey.com/en/products/detail/te-connectivity-amp-connectors/2-2387405-2/15221995)    |
| JP1           | 2PH1-02-UA              |        1 |        N/A | PinHeader_1x02_P2.00mm_Vertical     | [DigiKey](https://www.digikey.com/en/products/detail/adam-tech/2PH1-02-UA/9830305)                         |
| R31 to R36    | RT0402FRE0733RL         |        6 |     33-Ohm | Resistor_SMD_R_0402_1005Metric      | [DigiKey](https://www.digikey.com/en/products/detail/yageo/RT0402FRE0733RL/1071963)                        |
| R51 to R56    | RT0402FRE0749R9L        |        6 |   49.9-Ohm | Resistor_SMD_R_0402_1005Metric      | [DigiKey](https://www.digikey.com/en/products/detail/yageo/RT0402FRE0749R9L/1072042)                       |
| R1            | RT0402FRE07475RL        |        1 |    475-Ohm | Resistor_SMD_R_0402_1005Metric      | [DigiKey](https://www.digikey.com/en/products/detail/yageo/RT0402FRE07475RL/1072032)                       |
| R2, R5        | RT0402FRE0751KL         |        2 |    51k-Ohm | Resistor_SMD_R_0402_1005Metric      | [DigiKey](https://www.digikey.com/en/products/detail/yageo/RT0402FRE0751KL/1072058)                        |
| L1, L2        | BLM15PX601SN1D          |        2 | 600@100MHz | Resistor_SMD_R_0402_1005Metric      | [DigiKey](https://www.digikey.com/en/products/detail/murata-electronics/BLM15PX601SN1D/4421102)            |
| C4            | KGM05AR71C103KH         |        1 |     0.01uF | Capacitor_SMD_C_0402_1005Metric     | [DigiKey](https://www.digikey.com/en/products/detail/kyocera-avx/KGM05AR71C103KH/563224)                   |
| C1, C2, C3    | KGM05AR51A104KH         |        3 |      0.1uF | Capacitor_SMD_C_0402_1005Metric     | [DigiKey](https://www.digikey.com/en/products/detail/kyocera-avx/KGM05AR51A104KH/563239)                   |
| C5            | CL21B105KAFNNNE         |        1 |        1uF | Capacitor_SMD_C_0805_2012Metric     | [DigiKey](https://www.digikey.com/en/products/detail/samsung-electro-mechanics/CL21B105KAFNNNE/3886724)    |
| J7, J8        | 2337019-1               |        2 | U.FL(UMCC) | U.FL_Hirose                         | [DigiKey](https://www.digikey.com/en/products/detail/te-connectivity-amp-connectors/2337019-1/9974052)     |
| Jumper        | SPN02SYBN-RC            |        1 |        N/A | 2mm Shunt                           | [DigiKey](https://www.digikey.com/en/products/detail/sullins-connector-solutions/SPN02SYBN-RC/927356)      |

**Optional**: [TC74Ax-3-3VAT](https://www.digikey.com/en/products/detail/microchip-technology/TC74A0-3-3VAT/442720) I2C Temperature Sensor for testing I2C.




## Assembly Notes

Use needle-nosed pliers to remove the PCIe x4 Connector's mounting post.

![Remove PCIe x4 CONNECTOR Mounting Post](img/PCIe_x4_CONN_Remove_Mounting_Post.jpg)

Three wire jumpers are needed to connect `3V3==3V3_PCIe`, `nPERST==RST`, and `nPRSNT1==nPRSNT2_x4`.




## PCB Layer Stackup

4-Layer PCB stackup taken from [JLCPCB](https://jlcpcb.com/capabilities/pcb-capabilities).

![PCB Layer Stackup](img/Layer_Stackup.png)

Differential Impedance parameters were calculated using the [DigiKey Online Calculator](https://www.digikey.com/en/resources/conversion-calculators/conversion-calculator-pcb-trace-impedance).

![PCB Differential Impedance Calculation](img/PCB_Impedance_0.30mm_0.18mm_on_0.21mm_7628.png)




