# Battery Cells Specification

## Overview

This document describes the lithium-ion battery cells used in the car battery pack. Each cell is the fundamental energy storage unit of the system.

## Specifications

- **Cell Type**: Cylindrical 21700 Lithium-Ion
- **Chemistry**: NMC (Nickel Manganese Cobalt)
- **Nominal Voltage**: 3.7V
- **Capacity**: 5000 mAh
- **Max Discharge Rate**: 10C
- **Operating Temperature**: -20°C to 60°C
- **Cycle Life**: 2000 cycles @ 80% DoD

## Cell Configuration

Cells are arranged in modules of 12 cells per module (4S3P configuration). See [Battery Modules](battery-modules.md) for more details on module assembly.

## Safety Features

- Internal PTC (Positive Temperature Coefficient) protection
- CID (Current Interrupt Device)
- Vent mechanism for pressure relief
- Monitored by [Battery Management System](bms.md)

## Thermal Considerations

Cell temperature is critical for performance and safety. See [Thermal Management System](../mechanical/thermal-management.md) for cooling system details.

## Related Documents

- [Battery Modules](battery-modules.md) - Module assembly using these cells
- [Battery Management System](bms.md) - Electronic control and monitoring
- [Thermal Management System](../mechanical/thermal-management.md) - Temperature control
