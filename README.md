# AIoT Mask DE10-Nano v2

![Hardware](https://img.shields.io/badge/Domain-Hardware-blue)
![PCB](https://img.shields.io/badge/Design-PCB-green)
![Platform](https://img.shields.io/badge/Platform-DE10--Nano-orange)
![Revision](https://img.shields.io/badge/Revision-Version%2012-red)
![License](https://img.shields.io/badge/License-CERN--OHL--S--2.0-lightgrey)

Hardware design repository for the **AIoT Mask DE10-Nano v2**.

This project is a stackable **Printed Circuit Board (PCB)** mask / shield for the **Terasic DE10-Nano**, developed for **Artificial Intelligence of Things (AIoT)** prototyping, bring-up, validation, and manufacturing handoff.

---

## Overview

The AIoT Mask DE10-Nano integrates:

- **OV2640** camera interface
- **AHT20** temperature and humidity sensor
- **BH1750** ambient light sensor
- **ESP32** connectivity gateway
- **DE10-Nano** as the main hardware platform

The platform is intended for:

- sensor bring-up
- camera bring-up
- **Field-Programmable Gate Array (FPGA)** interfacing
- **Universal Asynchronous Receiver/Transmitter (UART)** data bridging
- **Message Queuing Telemetry Transport (MQTT)** publishing
- laboratory practice
- hardware design review
- manufacturing preparation

---

## Key Features

- Stackable shield / mask architecture for **DE10-Nano**
- 8-bit **OV2640** camera interface
- Shared **Inter-Integrated Circuit (I2C)** sensor bus for **AHT20** and **BH1750**
- Dedicated **Serial Camera Control Bus (SCCB)** control path for camera configuration
- Separate runtime **UART** and ESP32 programming path
- Structured documentation package for lab use and engineering handoff
- Included fabrication outputs and supporting design assets

---

## Interface Summary

### Sensor Path
- Shared **Inter-Integrated Circuit (I2C)** bus
- Devices:
  - **AHT20**
  - **BH1750**
- Typical working point:
  - **100 kHz**
- Common maximum operating point:
  - **400 kHz**

### Camera Path
- `CAM_D0 ... CAM_D7`
- `CAM_PCLK`
- `CAM_HSYNC`
- `CAM_VSYNC`
- `CAM_XCLK`
- `SCCB_SDA`
- `SCCB_SCL`

### ESP32 Path
- Dedicated runtime **Universal Asynchronous Receiver/Transmitter (UART)**
- Separate **ESP32 UART0** reserved for programming and debug
- Target runtime baud rate:
  - **921600**

---

## Clock and Power Notes

### Clock Notes
- `CAM_XCLK = 24 MHz`
- `CAM_PCLK` can reach approximately `36 MHz`

### Power Rails
- `V5_IN` — input rail from DE10-Nano
- `V3V3_SYS` — main 3.3 V system rail
- `V3V3_CAM` — camera-side 3.3 V branch
- `V2V8_CAM` — camera 2.8 V rail
- `V1V2_CAM` — camera core 1.2 V rail

---

## Repository Structure

```text
BOARD/       PCB board files
BOM/         Bill of Materials
DATASHEET/   Reference datasheets
FOOTPRINT/   PCB footprint libraries
GERBER/      Manufacturing outputs
Manual/      Lab manuals and mapping documents
NETLIST/     Netlist files
SCHEMATIC/   Schematic-related files
SYMBOL/      Schematic symbol libraries
README.md    Repository overview
LICENSE      License file
Documentation Package

The Manual/ folder contains supporting documents for bring-up, validation, and teaching:

AIoT_Vision_Mask_Lab_Manual.docx

AIoT_Vision_Mask_PinMap_Freeze.pdf

AIoT_Vision_Mask_Frequency_Map.pdf

AIoT_Vision_Mask_Current_Map.pdf

These documents support:

pin mapping freeze

operating frequency reference

current budgeting

student bring-up flow

engineering review and handoff

Online 3D Preview

You can inspect the current board in the JLCPCB 3D viewer here:

Open 3D board view

Recommended Bring-Up Flow

Verify power rails and ground continuity

Verify DE10-Nano header mapping

Verify ESP32 power and programming access

Verify runtime Universal Asynchronous Receiver/Transmitter (UART) link

Verify shared Inter-Integrated Circuit (I2C) sensor bus

Read AHT20 and BH1750

Verify camera clock and synchronization signals

Bring up OV2640

Validate end-to-end forwarding through Message Queuing Telemetry Transport (MQTT)

Manufacturing Status

This repository includes files intended for:

hardware design review

Printed Circuit Board (PCB) fabrication preparation

documentation handoff

Bill of Materials (BOM) review

3D inspection

Before fabrication, always verify:

latest GERBER/ outputs

latest BOARD/ source files

connector orientation

power rail naming consistency

mounting and mechanical alignment

pin mapping freeze documents

Revision Information

Repository: aiot-mask-de10-nano-v2

Hardware package: Version 12

Project type: DE10-Nano expansion mask / shield

Status: Prototype

Maintainer

ctw-design-team

License

This project is licensed under the CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S-2.0).
See the LICENSE file for the full license text.
