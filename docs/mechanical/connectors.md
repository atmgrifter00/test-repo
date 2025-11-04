# Connectors and Interface Specifications

## Overview

This document specifies all external electrical and mechanical connectors used to interface the battery pack with the vehicle and [charging system](../electrical/charging-system.md).

## High Voltage Connectors

### Main Power Output (HV+/HV-)
- **Type**: REMA 320A high-voltage connector
- **Rating**: 450V DC, 320A continuous, 500A peak
- **Pins**: 2-pin (positive and negative)
- **Color**: Orange housing (HV warning color)
- **Interlock**: Mechanical key prevents insertion under load
- **Locking**: Quarter-turn bayonet with audible click
- **Sealing**: IP67 when mated, IP6K9K with dust cap
- **Connection**: To motor inverter via [power distribution](../electrical/power-distribution.md)

### Charge Port Interface
- **AC Charging**: SAE J1772 Type 1 connector
- **DC Fast Charging**: CCS Combo 1 inlet
- **Location**: Vehicle left rear quarter panel
- **Features**: 
  - Locking mechanism (electronically controlled)
  - LED ring indicator (charge status)
  - Temperature monitoring
  - Integration with [charging system](../electrical/charging-system.md)

## Low Voltage Connectors

### BMS Communication Connector
- **Type**: Deutsch DTM 12-pin connector
- **Rating**: 13A per pin at 12V
- **Pins**:
  - Pin 1-2: CAN High/Low ([BMS](../core/bms.md) to vehicle)
  - Pin 3-4: 12V power and ground
  - Pin 5-6: Interlock loop
  - Pin 7-8: Emergency shutdown signal
  - Pin 9-10: Spare
  - Pin 11-12: Shield/chassis ground
- **Sealing**: IP67 with backshell
- **Cable**: Shielded twisted-pair, automotive grade

### Service Diagnostic Connector
- **Type**: 6-pin Mini-DIN
- **Location**: External to [enclosure](enclosure.md)
- **Interface**: USB-to-serial adapter compatible
- **Function**: [Monitoring system](../electrical/monitoring.md) access
- **Protection**: Cover with tether
- **Voltage**: 5V logic level

## Cooling System Connectors

### Coolant Quick-Disconnects
- **Type**: Stäubli RBE06 series
- **Size**: 3/4 inch (19mm)
- **Quantity**: 2 (inlet and outlet)
- **Features**:
  - Dry-break design (no spill on disconnect)
  - Flat-face connection
  - Auto-locking with visual confirmation
- **Connection**: To vehicle [thermal management](thermal-management.md) loop

### Thermal System Electrical
- **Type**: AMP Superseal 1.5 series, 4-pin
- **Pins**:
  - Pin 1-2: Pump power (12V, 5A)
  - Pin 3-4: Heater control (12V PWM signal)
- **Sealing**: IP67

## Internal Connectors

### Module Interconnects
- **Type**: Custom copper bus bars with bolted connections
- **Current**: 250A continuous per connection
- **Torque**: 10 Nm (M8 hardware)
- **Protection**: Insulation sleeves over exposed conductors
- **Connection**: Between [battery modules](../core/battery-modules.md)

### Module Sense Harness
- **Type**: Molex MicroFit 3.0, 16-position
- **Per Module**: Voltage sense wires to [BMS](../core/bms.md)
- **Wire**: 22 AWG, twisted pair, shielded
- **Pins**: 12 cell voltages + 3 temperature + ground

### BMS Internal Power
- **Type**: TE Connectivity AMP Econoseal, 4-pin
- **Pins**:
  - Pin 1-2: 12V supply from [power distribution](../electrical/power-distribution.md)
  - Pin 3-4: Ground and chassis ground
- **Rating**: 10A

## Connector Maintenance

### Inspection Schedule
- Visual inspection: Every 12 months
- Contact resistance measurement: Every 24 months  
- Seal integrity test: Every 24 months
- Replacement intervals per manufacturer specification

### Service Procedures
- All HV connectors: Service disconnect must be open
- Torque verification on bus bar connections: Annual
- Cleaning: Contact cleaner, no petroleum-based solvents
- Lubrication: Dielectric grease on gaskets only

## Safety Considerations

All connectors follow guidelines from [Safety Systems](../electrical/safety-systems.md):
- High-voltage connectors use orange color coding
- Touch-proof design (fingers cannot reach live parts)
- Interlock circuits prevent energization when disconnected
- First responder documentation includes connector locations

## Connector Torque Specifications

| Connection Type | Torque | Hardware |
|----------------|--------|----------|
| Module bus bars | 10 Nm | M8 bolt |
| Main HV output | 8 Nm | M6 bolt |
| BMS mounting | 1.5 Nm | M4 screw |
| Enclosure ground | 5 Nm | M6 bolt |
| Sense harness | Hand-tight | Molex lock |

## Related Documents

- [Battery Modules](../core/battery-modules.md) - Internal connections
- [Battery Management System](../core/bms.md) - Communication interfaces
- [Power Distribution](../electrical/power-distribution.md) - HV connections
- [Charging System](../electrical/charging-system.md) - Charge port
- [Safety Systems](../electrical/safety-systems.md) - Interlock requirements
- [Thermal Management](thermal-management.md) - Coolant connections
- [Enclosure Design](enclosure.md) - Connector mounting locations
