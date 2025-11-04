# Battery Thermal Management System

## Document Information
- **Document ID**: BAT-THRM-003
- **Version**: 1.0
- **Date**: 2025-11-04
- **Author**: Thermal Engineering Team
- **Status**: Draft

## 1. Introduction

This document defines the thermal management system design, requirements, and specifications for maintaining optimal battery temperature during all operating conditions.

## 2. System Purpose

The thermal management system shall:
- Maintain battery cells within optimal temperature range
- Minimize temperature gradients across the pack
- Provide heating in cold conditions
- Provide cooling during high-power operation and charging
- Prevent thermal runaway propagation

## 3. Temperature Requirements

### 3.1 Operating Temperature Ranges

| Condition | Minimum | Optimal | Maximum | Unit |
|-----------|---------|---------|---------|------|
| Cell Operating Temperature | -20 | 15 to 35 | 55 | °C |
| Continuous Operation | -10 | 20 to 30 | 45 | °C |
| Peak Power Operation | 0 | 20 to 30 | 40 | °C |
| Charging (AC) | -10 | 15 to 35 | 45 | °C |
| DC Fast Charging | 10 | 20 to 30 | 40 | °C |
| Storage (short-term) | -20 | 15 to 25 | 50 | °C |
| Storage (long-term) | -30 | 15 to 25 | 60 | °C |

### 3.2 Temperature Limits

| Limit Type | Value | Action | Unit |
|------------|-------|--------|------|
| Maximum Cell Temperature | 55 | Power deration starts | °C |
| Over-temperature Warning | 58 | Warning to driver | °C |
| Over-temperature Protection | 60 | Power limited to 25% | °C |
| Over-temperature Fault | 65 | Contactors open, system shutdown | °C |
| Minimum Cell Temperature | -20 | Normal operation limit | °C |
| Under-temperature Warning | -25 | Warning to driver | °C |
| Under-temperature Protection | -30 | Charging disabled | °C |

### 3.3 Temperature Uniformity

| Parameter | Value | Conditions | Unit |
|-----------|-------|------------|------|
| Maximum cell-to-cell ΔT | 5 | Steady-state operation | °C |
| Maximum cell-to-cell ΔT | 10 | Transient (30 seconds) | °C |
| Maximum module-to-module ΔT | 3 | Steady-state operation | °C |
| Maximum temperature gradient within cell | 3 | Per cell | °C |

## 4. Thermal Management System Architecture

### 4.1 Cooling System Type
- Primary: Liquid cooling with water/glycol mixture (50/50)
- Configuration: Bottom cooling plates with direct contact to cells
- Topology: Series-parallel flow with 3 parallel paths

### 4.2 Cooling System Components

1. **Cooling Plates**
   - Material: Aluminum with optimized channel design
   - Thermal interface: Phase change material (PCM) or thermal pad
   - Thermal conductivity: ≥ 3 W/mK
   - Contact area: ≥ 80% of cell bottom surface

2. **Coolant Pump**
   - Type: Electric centrifugal pump
   - Flow rate: 15 LPM (nominal), 20 LPM (maximum)
   - Pressure: 1.5 bar (nominal), 2.5 bar (maximum)
   - Power consumption: ≤ 150W

3. **Heat Exchanger/Chiller**
   - Type: Liquid-to-refrigerant heat exchanger
   - Cooling capacity: 15 kW at 40°C ambient
   - Integration: Vehicle HVAC system

4. **Expansion Tank**
   - Capacity: 1.5 liters
   - Pressure relief: 3 bar

### 4.3 Heating System

1. **Heating Elements**
   - Type: PTC (Positive Temperature Coefficient) heaters
   - Power: 5 kW total capacity
   - Location: Integrated in cooling plates
   - Control: PWM modulation

2. **Heating Strategy**
   - Pre-conditioning: Heat battery before cold start
   - Operating heating: Maintain minimum temperature during operation
   - Fast charge heating: Pre-heat for DC fast charging below 10°C

## 5. Temperature Sensor Specifications

### 5.1 Sensor Distribution

| Location | Quantity | Purpose |
|----------|----------|---------|
| Cell surface | 54 | Direct cell monitoring (1 per 4 cells) |
| Module terminals | 24 | Busbar temperature monitoring |
| Coolant inlet | 3 | Inlet temperature per path |
| Coolant outlet | 3 | Outlet temperature per path |
| Ambient | 2 | Reference and redundancy |

### 5.2 Sensor Specifications

| Parameter | Value | Unit |
|-----------|-------|------|
| Sensor Type | NTC Thermistor, 10kΩ at 25°C | - |
| Accuracy | ±2°C | °C |
| Resolution | 0.1°C | °C |
| Response Time (63%) | ≤ 3 | seconds |
| Measurement Range | -40 to +125 | °C |
| Update Rate | 1 | Hz |

## 6. Cooling Performance Requirements

### 6.1 Steady-State Cooling

| Operating Condition | Heat Generation | Required Cooling | Ambient Temp | Unit |
|---------------------|-----------------|------------------|--------------|------|
| Highway Driving | 8 | 8 | 35 | kW |
| City Driving | 5 | 5 | 35 | kW |
| Fast Charging (150kW) | 10 | 10 | 40 | kW |
| Fast Charging (100kW) | 6 | 6 | 40 | kW |

### 6.2 Transient Cooling

| Scenario | Duration | Peak Heat | Required Response | Unit |
|----------|----------|-----------|-------------------|------|
| Peak Power Discharge | 10 | 15 | Maintain T < 45°C | kW, s |
| Repeated Acceleration | 300 | 12 | Maintain T < 50°C | kW, s |
| Track Mode | 600 | 10 | Maintain T < 55°C | kW, s |

### 6.3 Coolant Flow Requirements

| Parameter | Minimum | Nominal | Maximum | Unit |
|-----------|---------|---------|---------|------|
| Flow Rate | 10 | 15 | 20 | LPM |
| Coolant Inlet Temperature | -10 | 20 | 45 | °C |
| Coolant Outlet Temperature | - | 30 | 50 | °C |
| ΔT across pack | - | 5 | 10 | °C |
| Pressure Drop | - | 0.3 | 0.8 | bar |

## 7. Heating Performance Requirements

### 7.1 Pre-heating

| Initial Temperature | Target Temperature | Time Limit | Power | Unit |
|---------------------|-------------------|------------|-------|------|
| -20 | 0 | 30 | 5 | °C, min, kW |
| -10 | 10 | 20 | 5 | °C, min, kW |
| 0 | 15 | 15 | 5 | °C, min, kW |

### 7.2 Operating Heating

- Maintain battery temperature above 0°C during operation
- Maximum heating power: 5 kW
- Heating shall not interfere with vehicle range by more than 5%

## 8. Thermal Control Strategies

### 8.1 Cooling Control

1. **Passive Cooling** (T < 35°C)
   - No active cooling required
   - Natural convection via coolant circulation

2. **Active Cooling Level 1** (35°C ≤ T < 40°C)
   - Coolant pump at 50% speed
   - Chiller at minimum capacity

3. **Active Cooling Level 2** (40°C ≤ T < 45°C)
   - Coolant pump at 75% speed
   - Chiller at 50% capacity

4. **Active Cooling Level 3** (T ≥ 45°C)
   - Coolant pump at 100% speed
   - Chiller at maximum capacity
   - Power deration if T > 50°C

### 8.2 Heating Control

1. **No Heating** (T > 15°C)
   - Heaters off

2. **Maintenance Heating** (10°C ≤ T ≤ 15°C)
   - Heaters at 30% power
   - Maintain temperature above 10°C

3. **Active Heating** (0°C ≤ T < 10°C)
   - Heaters at 60% power
   - Rapid warm-up for performance

4. **Maximum Heating** (T < 0°C)
   - Heaters at 100% power
   - Priority heating for minimal functionality

### 8.3 Temperature Balancing

- Monitor and minimize temperature differences between cells
- Adjust coolant flow distribution if module temperatures differ by > 3°C
- Implement cell-level monitoring for early detection of thermal anomalies

## 9. Thermal Runaway Prevention

### 9.1 Detection

- Temperature rise rate monitoring: Alert if > 5°C/min
- Cell voltage monitoring: Rapid voltage drop indication
- Pressure monitoring: Optional pressure sensors in pack

### 9.2 Mitigation

- Cell-to-cell thermal barriers: Prevent propagation for ≥ 5 minutes
- Automatic cooling system activation at maximum capacity
- Contactor opening to isolate electrical energy
- Driver warning and safe-stop request

### 9.3 Propagation Prevention

- Thermal barrier material between modules
- Propagation prevention: System shall contain thermal runaway to single module
- Vent gas management: Directed venting away from occupants

## 10. Thermal Interface Materials

### 10.1 Cell-to-Cooling Plate Interface

| Parameter | Specification | Unit |
|-----------|--------------|------|
| Material Type | Gap filler pad or phase change material | - |
| Thermal Conductivity | ≥ 3 | W/mK |
| Thickness | 0.5 to 2 | mm |
| Compression | 20-30 | % |
| Operating Temperature | -40 to +100 | °C |
| Service Life | 10 years minimum | - |

### 10.2 Module-to-Structure Interface

| Parameter | Specification | Unit |
|-----------|--------------|------|
| Material Type | Thermal interface pad | - |
| Thermal Conductivity | ≥ 1 | W/mK |
| Electrical Isolation | Required | - |

## 11. Coolant Specifications

### 11.1 Coolant Properties

| Property | Specification | Unit |
|----------|--------------|------|
| Type | Water/Glycol 50/50 mix | - |
| Freezing Point | -37 | °C |
| Boiling Point | 106 | °C |
| Specific Heat | 3.5 | kJ/kg·K |
| Thermal Conductivity | 0.4 | W/mK |
| Service Life | 5 years or 150,000 km | - |

### 11.2 System Volume

- Total coolant volume: 5 liters
- Battery pack volume: 3.5 liters
- System volume (including lines): 1.5 liters

## 12. Testing and Validation

### 12.1 Thermal Performance Testing

- Steady-state cooling capacity at 35°C, 40°C ambient
- Transient response to peak power events
- Heating performance at -20°C, -10°C, 0°C ambient
- Temperature uniformity under various operating conditions

### 12.2 Environmental Testing

- Thermal cycling: -30°C to +60°C, 100 cycles
- Hot soak: 8 hours at 60°C
- Cold soak: 8 hours at -30°C
- Humidity: 95% RH at 40°C, 48 hours

### 12.3 Durability Testing

- Coolant pump life test: 5000 hours
- Thermal interface material aging: 10 years equivalent
- Coolant degradation: 5 years equivalent

## 13. Maintenance Requirements

### 13.1 Coolant Maintenance

- Coolant level check: Every 12 months
- Coolant replacement: Every 5 years or 150,000 km
- pH level monitoring: Maintain 7.5 - 9.5
- Contamination check: Visual inspection annually

### 13.2 System Inspection

- Leak inspection: Every 12 months
- Temperature sensor calibration verification: Every 24 months
- Pump performance verification: Every 24 months
