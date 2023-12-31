**Work-In-Progress**: [Gerbers ready but not yet ordered](https://github.com/mwrnd/OpenCAPI-to-PCIe_x4_Host_and_Endpoint/releases/tag/v0.1-alpha).




# OpenCAPI to PCIe x4 Host and Endpoint

Designed to test simultaneous PCIe Host and Endpoint operation with the Innova-2.

There are two [PCIE4](https://docs.xilinx.com/r/en-US/pg213-pcie4-ultrascale-plus/Introduction) blocks in the column of the Innova-2's OpenCAPI Quads.

![Innova-2 OpenCAPI Banks](img/Innova2_OpenCAPI_XCKU15P_FFVE1517_Banks.png)

[OpenCAPI](https://files.openpower.foundation/s/xSQPe6ypoakKQdq/download/25Gbps-spec-20171108.pdf)-compatible SlimSAS 8x uses a **Host** version of the OpenCAPI **Carrier** pinout from the [ADM-PCIE-9V5 User Manual (Pg15-19of38)](https://www.alpha-data.com/xml/user_manuals/adm-pcie-9v5%20user%20manual_v1_4.pdf).




# PCB Layout

All differential pairs are length-matched to within 1mm intra-pair (N-to-P) and each group of differential pairs (e.g., TX0-to-TX4) is similarly matched to within 1mm.

![OpenCAPI to PCIe Host and Endpoint PCB Layout](img/OpenCAPI_PCIe_x4_Host_and_Endpoint_PCB_Layout.png)




# Schematic

![OpenCAPI to PCIe Host and Endpoint Schematic](img/OpenCAPI_PCIe_x4_Host_and_Endpoint_Schematic.png)




# Bill Of Materials

**Work-In-Progress**




# PCB Layer Stackup

4-Layer PCB stackup taken from [JLCPCB](https://jlcpcb.com/capabilities/pcb-capabilities).

![PCB Layer Stackup](img/Layer_Stackup.png)

Differential Impedance parameters were calculated using the [DigiKey Online Calculator](https://www.digikey.com/en/resources/conversion-calculators/conversion-calculator-pcb-trace-impedance).

![PCB Differential Impedance Calculation](img/PCB_Impedance_0.30mm_0.18mm_on_0.21mm_7628.png)




