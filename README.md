# SimpleCANBreakoutMicro

A tiny (20 × 15 mm) CAN transceiver breakout. It converts a microcontroller's logic-level CAN TX/RX to a CAN bus on a JST-GH connector, with an onboard 3.3 V regulator and optional 120 Ω termination.

Designed in KiCad 10.

## Features

- SN65HVD230 3.3 V CAN transceiver, wired for high-speed mode (up to 1 Mbps)
- XC6206 3.3 V LDO, so the board runs from a single 5 V supply
- 120 Ω termination resistor, enabled by a solder jumper (open by default)
- 2-layer, 1.6 mm PCB, parts on the top side only

## Connectors

**J1 — MCU side** (1×4 pin header, 2.54 mm)

| Pin | Signal |
|-----|--------|
| 1   | CAN RX |
| 2   | CAN TX |
| 3   | +5V    |
| 4   | GND    |

**J2 — CAN bus** (JST-GH 4-pin, SM04B-GHS-TB)

| Pin | Signal |
|-----|--------|
| 1   | +5V    |
| 2   | CANH   |
| 3   | CANL   |
| 4   | GND    |

The +5V pins on J1 and J2 are connected, so the board can be powered from either side. CAN TX/RX are 3.3 V logic.

## Termination

Bridge **JP1** (bottom side) to connect the 120 Ω resistor across CANH/CANL. Do this only if the board sits at an end of the bus.

## Bill of materials

| Ref        | Value      | Package            | LCSC    |
|------------|------------|--------------------|---------|
| U3         | SN65HVD230 | SOIC-8             | C12084  |
| U2         | XC6206 3.3 V | SOT-23-3         | C5446   |
| C1, C4, C5 | 1 µF       | 0603               |         |
| C2, C3, C6 | 100 nF     | 0603               |         |
| R1         | 120 Ω      | 0603               |         |
| J1         | 1×4 header | 2.54 mm            |         |
| J2         | JST-GH 4-pin | SM04B-GHS-TB     | C189895 |

## Files

- `SimpleCANBreakoutMicro.kicad_sch` / `.kicad_pcb` / `.kicad_pro` — KiCad project
- `production/` — fabrication outputs generated with the [Fabrication Toolkit](https://github.com/bennymeg/Fabrication-Toolkit) plugin: Gerbers and drill files (`SimpleCANBreakoutMicro.zip`), BOM, and pick-and-place positions, ready for JLCPCB
