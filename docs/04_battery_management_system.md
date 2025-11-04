# Battery Management System (BMS) Design Specification

## Document Information
- **Document ID**: BAT-BMS-004
- **Version**: 1.0
- **Date**: 2025-11-04
- **Author**: Controls Engineering Team
- **Status**: Draft

## 1. Introduction

This document specifies the Battery Management System (BMS) design, functionality, and requirements. The BMS is responsible for monitoring, controlling, and protecting the battery pack to ensure safe and optimal operation.

## 2. System Overview

### 2.1 Purpose

The BMS shall:
- Monitor cell voltages, currents, and temperatures
- Estimate state of charge (SOC) and state of health (SOH)
- Balance cell voltages
- Control thermal management system
- Implement safety protection functions
- Communicate with vehicle control systems
- Log diagnostic and operational data

### 2.2 Architecture

- **Master BMS**: Central control unit with main processing and communication
- **Slave BMS Units**: Cell monitoring boards (1 per module, 12 total)
- **Current Sensor**: High-precision current measurement
- **Isolation Monitoring**: HV isolation detection
- **Contactor Control**: HV circuit control

## 3. Hardware Specifications

### 3.1 Master BMS Controller

| Parameter | Specification |
|-----------|--------------|
| Microcontroller | 32-bit ARM Cortex-M7, ≥180 MHz |
| Flash Memory | ≥2 MB |
| RAM | ≥512 KB |
| EEPROM/NVM | ≥128 KB |
| Operating Voltage | 9-16V (12V nominal) |
| Power Consumption | ≤5W (typical), ≤10W (max) |
| Operating Temperature | -40°C to +85°C |

### 3.2 Slave BMS Modules

| Parameter | Specification |
|-----------|--------------|
| Cell Monitoring IC | Multi-cell AFE (Analog Front End) |
| Cells per Module | 18 cells |
| Voltage Measurement Channels | 18 per module |
| Temperature Inputs | 6 per module (analog NTC) |
| Cell Balancing | Passive balancing, 200mA per cell |
| Communication | Isolated daisy-chain or CAN |
| Operating Temperature | -40°C to +85°C |

### 3.3 Current Sensor

| Parameter | Specification |
|-----------|--------------|
| Technology | Hall-effect or Shunt-based |
| Measurement Range | ±500A |
| Accuracy | ±0.5% of reading |
| Resolution | 0.1A |
| Response Time | ≤10 ms |
| Isolation | ≥3 kV |

### 3.4 Voltage Isolation Monitor

| Parameter | Specification |
|-----------|--------------|
| Measurement Range | 0-1000V DC |
| Isolation Resistance Detection | 0-10 MΩ |
| Response Time | ≤1 second |
| Accuracy | ±10% |

## 4. Software Architecture

### 4.1 Software Modules

1. **Cell Monitoring Module**
   - Voltage acquisition
   - Temperature acquisition
   - Data filtering and validation

2. **State Estimation Module**
   - SOC estimation
   - SOH estimation
   - Power capability estimation
   - Energy calculation

3. **Protection Module**
   - Over/under voltage protection
   - Over-current protection
   - Over/under temperature protection
   - Isolation fault detection

4. **Cell Balancing Module**
   - Balancing algorithm
   - Balancing control
   - Balance state monitoring

5. **Thermal Management Module**
   - Cooling control
   - Heating control
   - Temperature optimization

6. **Communication Module**
   - CAN communication
   - Diagnostic protocol
   - Data logging

7. **Diagnostics Module**
   - Fault detection
   - Fault logging
   - Self-test routines

### 4.2 Software Safety

- MISRA C compliance for critical functions
- ASIL-D capable architecture
- Software watchdog implementation
- Memory protection mechanisms
- Safe state transitions

## 5. Measurement Specifications

### 5.1 Voltage Measurement

| Parameter | Specification | Unit |
|-----------|--------------|------|
| Cell Voltage Range | 2.0 to 4.5 | V |
| Accuracy | ±10 | mV |
| Resolution | 1 | mV |
| Sample Rate | 10 | Hz |
| Pack Voltage Range | 0 to 500 | V |
| Pack Voltage Accuracy | ±0.5% | of reading |

### 5.2 Current Measurement

| Parameter | Specification | Unit |
|-----------|--------------|------|
| Measurement Range | -500 to +500 | A |
| Accuracy | ±0.5% | of reading |
| Resolution | 0.1 | A |
| Sample Rate | 100 | Hz |
| Offset Error | ±0.1 | A |
| Coulomb Counting Accuracy | ±2% | over full range |

### 5.3 Temperature Measurement

| Parameter | Specification | Unit |
|-----------|--------------|------|
| Measurement Range | -40 to +125 | °C |
| Accuracy | ±2 | °C |
| Resolution | 0.1 | °C |
| Sample Rate | 1 | Hz |
| Number of Sensors | 72 | - |

### 5.4 Isolation Resistance Measurement

| Parameter | Specification | Unit |
|-----------|--------------|------|
| Measurement Range | 0 to 10 | MΩ |
| Accuracy | ±10% | - |
| Resolution | 1 | kΩ |
| Measurement Frequency | 0.1 | Hz (continuous) |
| Warning Threshold | 200 | Ω/V |
| Fault Threshold | 100 | Ω/V |

## 6. State Estimation

### 6.1 State of Charge (SOC) Estimation

| Parameter | Specification |
|-----------|--------------|
| Algorithm | Adaptive Coulomb Counting + Kalman Filter |
| Initialization Method | Open-circuit voltage lookup |
| Accuracy | ±3% (typical), ±5% (max) |
| Update Rate | 1 Hz |
| SOC Range | 0-100% |
| Resolution | 0.1% |

**SOC Estimation Requirements:**
- Compensate for temperature effects
- Account for aging/capacity fade
- Reset based on voltage at rest
- Handle charge/discharge efficiency variations

### 6.2 State of Health (SOH) Estimation

| Parameter | Specification |
|-----------|--------------|
| Algorithm | Capacity-based + impedance-based |
| Accuracy | ±5% |
| Update Frequency | Per full charge cycle |
| SOH Range | 0-100% |
| Resolution | 1% |

**SOH Indicators:**
- Capacity fade relative to beginning-of-life
- Internal resistance increase
- Self-discharge rate changes
- Charge acceptance degradation

### 6.3 Power Capability Estimation

| Parameter | Specification |
|-----------|--------------|
| Algorithm | Voltage and thermal limit based |
| Update Rate | 1 Hz |
| Accuracy | ±10% |
| Look-ahead Time | 10 seconds |

**Power Limits Based On:**
- Current SOC
- Cell voltage limits
- Temperature limits
- Cell voltage balance
- SOH degradation

### 6.4 Energy Calculation

| Parameter | Specification |
|-----------|--------------|
| Available Energy | Calculated from SOC and capacity |
| Accuracy | ±5% |
| Update Rate | 1 Hz |
| Display Resolution | 1 kWh |

## 7. Cell Balancing

### 7.1 Balancing Specifications

| Parameter | Specification | Unit |
|-----------|--------------|------|
| Balancing Method | Passive (resistive) | - |
| Balancing Current | 200 | mA/cell |
| Balancing Threshold | 50 | mV |
| Target Balance | 10 | mV |
| Maximum Balancing Time | 12 | hours |

### 7.2 Balancing Strategy

**Active Balancing Conditions:**
- During charging (SOC > 80%)
- At rest when cell imbalance > 50mV
- Before high-power operations if imbalance > 30mV

**Balancing Algorithm:**
1. Identify cells above average voltage
2. Enable balancing for cells > (Vavg + threshold)
3. Continue until all cells within target balance
4. Disable at discharge or high temperature (>45°C)

### 7.3 Balancing Performance

- Maximum imbalance after balancing: 10 mV
- Balancing energy dissipation: ≤100W total
- Balancing efficiency: N/A (passive)

## 8. Protection Functions

### 8.1 Voltage Protection

| Protection Type | Threshold | Delay | Response |
|----------------|-----------|-------|----------|
| Cell Over-voltage Warning | 4.20V | 1s | Warning message |
| Cell Over-voltage Protection | 4.25V | 0.5s | Reduce power, open contactors if charging |
| Cell Over-voltage Fault | 4.30V | 0.1s | Open contactors immediately |
| Cell Under-voltage Warning | 2.80V | 1s | Warning message |
| Cell Under-voltage Protection | 2.70V | 0.5s | Reduce power |
| Cell Under-voltage Fault | 2.50V | 0.1s | Open contactors immediately |

### 8.2 Current Protection

| Protection Type | Threshold | Delay | Response |
|----------------|-----------|-------|----------|
| Discharge Over-current Warning | 400A | 15s | Warning message |
| Discharge Over-current Protection | 700A | 3s | Reduce power to 50% |
| Discharge Over-current Fault | 800A | 0.1s | Open contactors |
| Charge Over-current Warning | 250A | 15s | Warning message |
| Charge Over-current Protection | 450A | 3s | Request charge power reduction |
| Charge Over-current Fault | 500A | 0.1s | Open contactors |

### 8.3 Temperature Protection

| Protection Type | Threshold | Delay | Response |
|----------------|-----------|-------|----------|
| Over-temperature Warning | 55°C | 5s | Warning, request cooling |
| Over-temperature Protection | 60°C | 2s | Limit power to 25% |
| Over-temperature Fault | 65°C | 0.5s | Open contactors |
| Under-temperature Warning | -20°C | 5s | Warning, request heating |
| Under-temperature Protection | -25°C | 2s | Limit power to 50% |
| Under-temperature Fault | -30°C | 0.5s | Disable charging |

### 8.4 Isolation Fault Protection

| Protection Type | Threshold | Delay | Response |
|----------------|-----------|-------|----------|
| Isolation Warning | 200 Ω/V | 5s | Warning message |
| Isolation Fault | 100 Ω/V | 1s | Open contactors, safe mode |

### 8.5 Communication Fault Protection

| Fault Type | Detection Time | Response |
|------------|---------------|----------|
| CAN bus timeout | 100ms | Enter safe mode, maintain last valid state |
| Slave BMS communication loss | 500ms | Use last valid data, warning after 2s |
| Sensor fault | 1s | Use redundant sensor or model-based estimate |

## 9. Contactor Control

### 9.1 Contactor Specifications

| Parameter | Specification |
|-----------|--------------|
| Number of Contactors | 2 (positive and negative) |
| Contactor Type | Normally open, double-break |
| Voltage Rating | 450V DC continuous, 900V withstand |
| Current Rating | 500A continuous, 1000A (30s) |
| Auxiliary Contacts | 2 NO + 2 NC per contactor |

### 9.2 Pre-charge Circuit

| Parameter | Specification |
|-----------|--------------|
| Pre-charge Resistor | 1kΩ, 50W |
| Pre-charge Relay | 450V DC, 10A |
| Pre-charge Time Target | ≤5 seconds |
| Pre-charge Complete Threshold | 90% of pack voltage |

### 9.3 Contactor Control Sequences

**Power-up Sequence:**
1. Verify isolation resistance > 100 Ω/V
2. Close pre-charge relay
3. Monitor voltage rise
4. When voltage ≥ 90% of pack voltage, close main contactors
5. Open pre-charge relay
6. Verify contactor closure via auxiliary contacts
7. Enable HV system

**Power-down Sequence:**
1. Reduce power to zero
2. Open main contactors
3. Verify contactor opening via auxiliary contacts
4. Discharge HV capacitors via bleed resistors
5. Verify voltage < 60V before allowing service

**Emergency Shutdown:**
1. Immediately open all contactors
2. Enter safe mode
3. Disable all charging/discharging
4. Maintain monitoring and communication

## 10. Communication Interfaces

### 10.1 CAN Bus Communication

| Parameter | Specification |
|-----------|--------------|
| Protocol | CAN 2.0B |
| Baud Rate | 500 kbps |
| Bus Load | ≤60% typical, ≤80% peak |
| Message Timeout | 100 ms |
| Number of Messages | 15 (transmit), 20 (receive) |

**Key CAN Messages (Transmit):**
- Battery status (SOC, SOH, voltage, current) - 10ms
- Battery limits (power, voltage, current) - 100ms
- Battery temperatures - 100ms
- Cell voltage statistics - 1000ms
- Isolation resistance - 1000ms
- Diagnostic status - 100ms

**Key CAN Messages (Receive):**
- Vehicle state - 10ms
- Charge control - 100ms
- Thermal management request - 100ms
- Diagnostic requests - As needed

### 10.2 Diagnostic Communication

| Parameter | Specification |
|-----------|--------------|
| Protocol | ISO 14229 (UDS) |
| Physical Layer | CAN or Ethernet |
| Security | Seed/key authentication |
| Services | Read/clear DTCs, read data, parameter setting |

### 10.3 Internal Communication

| Parameter | Specification |
|-----------|--------------|
| Master-Slave Protocol | Isolated SPI or daisy-chain |
| Update Rate | 10 Hz for voltages/temperatures |
| Fault Detection | Communication timeout < 500ms |

## 11. Data Logging and Diagnostics

### 11.1 Continuous Data Logging

**Logged Parameters (1 Hz):**
- Pack voltage, current, power
- SOC, SOH
- Minimum/maximum/average cell voltages
- Minimum/maximum/average temperatures
- Isolation resistance
- Contactor states

**Storage Requirements:**
- Minimum 30 days of continuous operation
- Non-volatile memory: 512 MB minimum
- Ring buffer implementation

### 11.2 Snapshot Data

**Event-triggered snapshots:**
- Protection events (all types)
- Contactor operations
- Communication faults
- Power-on/off events

**Snapshot Data:**
- All monitored parameters at event time
- ±10 seconds of data around event
- Time stamp and event type

### 11.3 Diagnostic Trouble Codes (DTCs)

**DTC Categories:**
- Voltage faults (over/under voltage)
- Current faults (over-current)
- Temperature faults (over/under temperature)
- Isolation faults
- Communication faults
- Hardware faults (sensor, contactor)
- Software faults (watchdog, memory)

**DTC Storage:**
- Current DTCs: Active faults
- Pending DTCs: Intermittent faults
- Historical DTCs: Last 100 faults with freeze frame

## 12. Functional Safety

### 12.1 Safety Requirements

- Functional safety level: ASIL-D capable
- Safety concept: ISO 26262 compliant
- Independent safety monitoring
- Dual-channel architecture for critical functions

### 12.2 Safety Mechanisms

**Hardware Safety:**
- Voltage measurement redundancy (per cell)
- Current measurement redundancy (dual sensors optional)
- Temperature sensor plausibility checks
- Contactor feedback monitoring
- Watchdog timer

**Software Safety:**
- Plausibility checks on all measurements
- Range checks on calculated values
- Sequence monitoring for state machines
- Memory integrity checks (CRC)
- Safe state definitions and transitions

### 12.3 Failure Mode Management

**Safe States:**
1. Normal Operation
2. Limited Operation (reduced power)
3. Emergency Operation (minimal function)
4. Safe Mode (contactors open, monitoring only)

**Failure Responses:**
- Single sensor failure: Use redundant or estimated value
- Communication failure: Maintain safe defaults
- Actuator failure: Open contactors, prevent operation
- Multiple failures: Enter safe mode immediately

## 13. Performance Requirements

### 13.1 Response Times

| Function | Response Time |
|----------|--------------|
| Voltage measurement update | 100 ms |
| Current measurement update | 10 ms |
| Temperature measurement update | 1 s |
| SOC update | 1 s |
| Protection response | 100 ms (critical), 1 s (non-critical) |
| Contactor control | 100 ms |
| CAN message transmission | 10 ms (critical), 100 ms (normal) |

### 13.2 Computational Requirements

| Function | Execution Time |
|----------|---------------|
| Voltage acquisition and processing | < 50 ms |
| Current acquisition and processing | < 5 ms |
| SOC estimation | < 100 ms |
| SOH estimation | < 1 s (background) |
| Protection checks | < 10 ms |
| Cell balancing control | < 100 ms |

## 14. Testing and Validation

### 14.1 Hardware Testing

- Voltage measurement accuracy verification
- Current measurement accuracy verification
- Temperature measurement accuracy verification
- Contactor operation verification
- Communication interface testing
- EMC testing per ISO 11452

### 14.2 Software Testing

- Unit testing: All software modules
- Integration testing: Module interactions
- System testing: Complete BMS functionality
- Safety testing: Fault injection, FMEA validation
- Performance testing: Real-time constraints

### 14.3 Functional Testing

- SOC estimation accuracy (various conditions)
- SOH estimation accuracy (aging simulation)
- Power capability accuracy
- Cell balancing effectiveness
- Protection function verification (all types)
- Communication protocol compliance

### 14.4 Environmental Testing

- Temperature cycling: -40°C to +85°C
- Vibration: ISO 16750-3
- Shock: ISO 16750-3
- EMC: ISO 11452-2, ISO 11452-4
- Humidity: 95% RH, 40°C, 48 hours
