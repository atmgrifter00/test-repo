# Monitoring System

## Overview

The monitoring system provides real-time visibility into battery pack status, working in conjunction with the [BMS](../core/bms.md) to present operational data to users and service technicians.

## Monitored Parameters

### Battery Status
- State of Charge (SoC): 0-100%
- State of Health (SoH): Battery degradation tracking
- Remaining range estimation
- Power capability (charge/discharge limits)
- Individual [cell voltages](../core/battery-cells.md)
- [Module temperatures](../core/battery-modules.md)

### Electrical Parameters
- Pack voltage (current, min, max)
- Pack current (instantaneous, average)
- Power flow (kW in/out)
- Energy throughput (kWh cumulative)
- [Charging status](charging-system.md) and estimated time

### Thermal Status
- Maximum/minimum/average cell temperatures
- [Coolant temperature](../mechanical/thermal-management.md)
- Cooling system status
- Thermal management requests

### Safety and Diagnostics
- Active fault codes from [BMS](../core/bms.md)
- [Safety system](safety-systems.md) status
- Contactor states ([power distribution](power-distribution.md))
- Insulation resistance
- Component health indicators

## User Interfaces

### Vehicle Dashboard Display
- SoC gauge (primary)
- Range estimate
- Power flow indicator
- Warning/fault indicators

### Mobile Application
- Detailed battery status
- Historical data and trends
- Charging session summaries
- Maintenance alerts

### Service Interface
- Diagnostic trouble codes (DTCs)
- Detailed cell-level data
- Calibration tools
- Data logging and export

## Communication Protocols

- **CAN Bus**: Primary communication with [BMS](../core/bms.md)
- **OBD-II**: Standard diagnostic port access
- **Bluetooth/WiFi**: Mobile app connectivity
- **Ethernet**: Service tool connection

## Data Logging

The monitoring system records:
- All [BMS](../core/bms.md) data at 1 Hz
- Fault events with timestamps
- Charging session details
- Temperature profiles
- 30-day rolling buffer in non-volatile memory

## Related Documents

- [Battery Management System](../core/bms.md) - Data source
- [Battery Cells](../core/battery-cells.md) - Cell-level monitoring
- [Battery Modules](../core/battery-modules.md) - Module-level sensing
- [Charging System](charging-system.md) - Charge monitoring
- [Safety Systems](safety-systems.md) - Fault reporting
- [Thermal Management](../mechanical/thermal-management.md) - Temperature data
