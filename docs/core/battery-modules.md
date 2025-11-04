# Battery Modules

## Overview

Battery modules are the intermediate level of organization in the battery pack, consisting of multiple [battery cells](battery-cells.md) arranged in a specific configuration.

## Module Specifications

- **Configuration**: 4S3P (4 series, 3 parallel)
- **Total Cells per Module**: 12 cells
- **Module Voltage**: 14.8V nominal (16.8V max, 12.0V min)
- **Module Capacity**: 15 Ah
- **Dimensions**: 280mm x 180mm x 65mm
- **Weight**: 2.1 kg

## Assembly

Each module contains:
- 12x [21700 cells](battery-cells.md) in plastic cell holders
- Module PCB with [BMS](bms.md) interface connectors
- Temperature sensors (NTC thermistors) at 3 locations
- Fusing for each parallel group
- Module-level voltage sensing connections

## Pack Configuration

The complete battery pack contains 24 modules arranged in 2P12S configuration, providing:
- **Pack Voltage**: 88.8V nominal (100.8V max, 72.0V min)
- **Pack Capacity**: 30 Ah
- **Total Energy**: 2.66 kWh

## Electrical Connections

Modules connect to the [Power Distribution System](../electrical/power-distribution.md) via high-current bus bars and to the [BMS](bms.md) via monitoring harnesses.

## Related Documents

- [Battery Cells](battery-cells.md) - Individual cell specifications
- [Battery Management System](bms.md) - Electronic monitoring and control
- [Power Distribution System](../electrical/power-distribution.md) - Electrical connections
- [Enclosure Design](../mechanical/enclosure.md) - Physical housing
