# Charging System

## Overview

The charging system manages the flow of electrical energy into the battery pack, coordinating with the [BMS](../core/bms.md) to ensure safe and optimal charging.

## Charging Specifications

### AC Charging (Level 2)
- **Input**: 240V AC, single-phase
- **Power**: 7.2 kW maximum
- **Charge Time**: 0-100% in ~3 hours
- **Connector**: J1772 standard

### DC Fast Charging (Level 3)
- **Input**: 400V DC
- **Power**: 50 kW maximum
- **Charge Time**: 20-80% in 30 minutes
- **Connector**: CCS (Combined Charging System)

## Charging Algorithm

The system uses a multi-stage charging profile:

1. **Bulk Stage**: Constant current at 1C rate until 80% SoC
2. **Absorption Stage**: Constant voltage at 100.8V until current drops to 0.1C
3. **Float Stage**: Reduced voltage for top-off and maintenance

All charging is controlled and monitored by the [BMS](../core/bms.md) to prevent overcharging of individual [cells](../core/battery-cells.md).

## Hardware Components

- **On-board Charger (OBC)**: AC-DC converter with PFC (Power Factor Correction)
- **DC-DC Converter**: For 12V auxiliary system charging
- **Charge Port**: Weather-sealed connector with locking mechanism
- **Inlet Thermal Management**: Integrated with [cooling system](../mechanical/thermal-management.md)

## Safety Features

- Input voltage monitoring
- Ground fault detection (GFCI)
- Over-temperature protection
- Emergency disconnect capability
- Coordinated with [Safety Systems](safety-systems.md)

## Communication

The charging system communicates with:
- [BMS](../core/bms.md) for charge control and limits
- Vehicle controller for user interface
- Charging station via pilot signal (AC) or CAN (DC)
- [Monitoring System](monitoring.md) for diagnostics

## Related Documents

- [Battery Management System](../core/bms.md) - Charge control
- [Battery Cells](../core/battery-cells.md) - Cell charging limits
- [Power Distribution](power-distribution.md) - Electrical connections
- [Safety Systems](safety-systems.md) - Protection mechanisms
- [Monitoring System](monitoring.md) - Charge status reporting
- [Thermal Management](../mechanical/thermal-management.md) - Cooling during charging
