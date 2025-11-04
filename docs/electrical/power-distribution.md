# Power Distribution System

## Overview

The power distribution system manages the flow of electrical power from the [battery modules](../core/battery-modules.md) to the vehicle's electric motor and auxiliary systems.

## Architecture

### High Voltage Distribution
- **Main Bus**: Copper bus bars (10mm x 50mm) rated for 300A continuous
- **Pack Voltage**: 88.8V nominal (72-100.8V range)
- **Maximum Discharge Current**: 250A continuous, 400A peak (30 seconds)
- **Service Disconnect**: Manual isolation switch for maintenance safety

### Contactors
The system uses three main contactors controlled by the [BMS](../core/bms.md):
- **Positive Contactor**: Main pack positive connection
- **Negative Contactor**: Main pack negative connection  
- **Pre-charge Contactor**: Soft-start circuit with resistor

### Pre-charge Circuit
To prevent inrush current when connecting the pack:
1. Pre-charge contactor closes with series resistor (100Ω, 50W)
2. Capacitors in downstream systems charge gradually
3. After voltage equilibration, main contactors close
4. Pre-charge contactor opens

## Fusing and Protection

- **Main Fuse**: 300A high-voltage fuse at pack output
- **Module Fuses**: Individual fusing per [module](../core/battery-modules.md)
- **Auxiliary Fuse**: 10A for BMS and monitoring circuits
- Coordinated with [Safety Systems](safety-systems.md)

## Cable Specifications

- **High Voltage Cables**: 50mm² orange-insulated automotive cable
- **Sense Wires**: Twisted pair, shielded 22 AWG to [BMS](../core/bms.md)
- **Shield Grounding**: Single-point ground at BMS end
- **Routing**: Secured in [enclosure](../mechanical/enclosure.md) with strain relief

## Voltage Levels

### High Voltage (HV)
- Battery pack output: 72-100.8V
- To motor inverter and [charging system](charging-system.md)

### Low Voltage (LV)  
- 12V auxiliary system via DC-DC converter (100W)
- Powers [BMS](../core/bms.md) and [monitoring](monitoring.md) systems

## Related Documents

- [Battery Modules](../core/battery-modules.md) - Power source
- [Battery Management System](../core/bms.md) - Contactor control
- [Charging System](charging-system.md) - Power input
- [Safety Systems](safety-systems.md) - Emergency isolation
- [Enclosure Design](../mechanical/enclosure.md) - Cable routing and mounting
