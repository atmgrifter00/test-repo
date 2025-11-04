# Thermal Management System

## Overview

The thermal management system maintains optimal temperature for all [battery cells](../core/battery-cells.md) and [modules](../core/battery-modules.md) across all operating conditions, crucial for performance, safety, and longevity.

## Design Philosophy

Lithium-ion cells operate optimally between 20-35°C. The thermal system must:
- Cool during fast discharge and charging
- Heat in cold ambient conditions
- Maintain uniform temperature across all cells
- Respond to [BMS](../core/bms.md) control commands

## System Architecture

### Active Liquid Cooling
- **Coolant**: 50/50 water-glycol mixture
- **Flow Rate**: 10 liters/minute
- **Operating Pressure**: 1.5 bar
- **Coolant Capacity**: 3.5 liters

### Cooling Plate Design
- Aluminum cold plate bonded to [enclosure](enclosure.md) base
- Serpentine flow channels (8mm diameter)
- Direct contact with module bases
- Thermal conductivity: >150 W/m·K

## Components

### Heat Exchanger
- Compact brazed-plate design
- Coolant-to-refrigerant heat exchange
- Integrated with vehicle HVAC system
- Capacity: 5 kW cooling, 3 kW heating

### Pump
- Electric coolant pump
- Variable speed control by [BMS](../core/bms.md)
- Flow rate: 0-15 LPM
- Power consumption: 50W nominal

### Valves and Plumbing
- 3-way valve for heating/cooling mode selection
- Pressure relief valve (3 bar threshold)
- Quick-disconnect couplings for service
- Rubber hoses with fire-resistant outer layer

### PTC Heater
- Positive Temperature Coefficient heating element
- Power: 2 kW
- Self-regulating to prevent overheating
- Activated in ambient temperatures <10°C

## Control Strategy

The [BMS](../core/bms.md) controls thermal management based on:

### Cooling Activation
- Cell temperature >35°C → Start cooling
- Fast charging → Pre-cooling activation
- High power discharge → Maximum cooling
- Temperature gradient >5°C → Increase flow

### Heating Activation  
- Cell temperature <10°C → Start heating
- Pre-conditioning before drive (if plugged in)
- During charging in cold weather
- Minimum charge temperature: 0°C

### Temperature Zones
Temperature limits enforced by [BMS](../core/bms.md):
- **Green Zone**: 20-35°C (optimal performance)
- **Yellow Zone**: 10-20°C or 35-45°C (reduced power)
- **Red Zone**: <10°C or >45°C (limited operation)
- **Critical**: <0°C or >55°C (shutdown if not recovering)

## Thermal Sensors

### Sensor Locations
- 3x NTC thermistors per [module](../core/battery-modules.md) (72 total)
- 2x coolant temperature sensors (inlet/outlet)
- 1x ambient air temperature sensor
- Accuracy: ±1°C from 0-50°C

### Monitoring
All sensor data reported to [monitoring system](../electrical/monitoring.md) for:
- Temperature distribution analysis
- Thermal anomaly detection
- Predictive maintenance
- Historical trending

## Performance Requirements

### Cooling Capability
- Maintain cells <45°C during 50 kW DC fast charging
- Reduce pack temperature from 45°C to 35°C in 10 minutes
- Handle 250A continuous discharge with <40°C cell temperature

### Heating Capability
- Raise pack temperature from 0°C to 10°C in 30 minutes (while plugged in)
- Maintain >5°C during winter operation
- Minimize energy consumption from battery

## Safety Integration

Coordinated with [Safety Systems](../electrical/safety-systems.md):
- Over-temperature protection (>60°C)
- Coolant leak detection
- Pump failure detection
- Thermal runaway mitigation

## Maintenance

- Coolant replacement every 4 years / 100k km
- Pressure test annually
- Hose inspection for cracks/leaks
- Filter cleaning every 2 years
- Pump performance test per service schedule

## Related Documents

- [Battery Cells](../core/battery-cells.md) - Temperature limits and requirements
- [Battery Modules](../core/battery-modules.md) - Module temperature sensors
- [Battery Management System](../core/bms.md) - Thermal control system
- [Charging System](../electrical/charging-system.md) - Cooling during charge
- [Monitoring System](../electrical/monitoring.md) - Temperature reporting
- [Safety Systems](../electrical/safety-systems.md) - Thermal protection
- [Enclosure Design](enclosure.md) - Cooling plate integration
