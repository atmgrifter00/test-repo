# Battery Electrical Specifications

## Document Information
- **Document ID**: BAT-ELEC-002
- **Version**: 1.0
- **Date**: 2025-11-04
- **Author**: Electrical Engineering Team
- **Status**: Draft

## 1. Introduction

This document specifies the electrical characteristics, performance parameters, and requirements for the car battery system.

## 2. Battery Cell Specifications

### 2.1 Cell Type
- Chemistry: Lithium Nickel Manganese Cobalt Oxide (NMC 811)
- Form Factor: Prismatic
- Manufacturer: Supplier A (qualified), Supplier B (qualified)

### 2.2 Cell Electrical Parameters

| Parameter | Minimum | Nominal | Maximum | Unit |
|-----------|---------|---------|---------|------|
| Voltage | 2.8 | 3.7 | 4.2 | V |
| Capacity | 95 | 100 | 105 | Ah |
| Energy | - | 370 | - | Wh |
| Internal Resistance | - | 0.8 | 1.2 | mΩ |

### 2.3 Cell Performance

| Parameter | Value | Conditions | Unit |
|-----------|-------|------------|------|
| Continuous Discharge Current | 3C | 25°C | A |
| Peak Discharge Current (10s) | 5C | 25°C | A |
| Continuous Charge Current | 1C | 25°C | A |
| Peak Charge Current (10s) | 2C | 25°C | A |
| Cycle Life | 2500 | 80% DOD, 25°C | cycles |

## 3. Battery Pack Configuration

### 3.1 Pack Architecture
- Module Configuration: 18 cells in series per module (18S)
- Pack Configuration: 6 modules in series, 2 strings in parallel (6S2P at module level)
- Total Cells: 216 cells (108S2P at cell level)
- Module Count: 12 modules total

### 3.2 Pack Voltage Specifications

| Parameter | Minimum | Nominal | Maximum | Unit |
|-----------|---------|---------|---------|------|
| Pack Voltage | 302.4 | 399.6 | 453.6 | V |
| Module Voltage | 50.4 | 66.6 | 75.6 | V |
| Operating Voltage Range | 320 | 399.6 | 420 | V |

### 3.3 Pack Capacity and Energy

| Parameter | Value | Unit |
|-----------|-------|------|
| Nominal Capacity | 200 | Ah |
| Nominal Energy | 79.92 | kWh |
| Usable Energy | 70 | kWh |
| Depth of Discharge (DOD) | 87.5 | % |

## 4. Power Characteristics

### 4.1 Discharge Power

| Parameter | Value | Duration | Conditions | Unit |
|-----------|-------|----------|------------|------|
| Maximum Continuous Power | 150 | Continuous | 25°C, 50% SOC | kW |
| Peak Power | 250 | 10s | 25°C, 50% SOC | kW |
| Power at 10% SOC | 120 | Continuous | 25°C | kW |
| Power at 90% SOC | 140 | Continuous | 25°C | kW |

### 4.2 Charge Power

| Parameter | Value | Duration | Conditions | Unit |
|-----------|-------|----------|------------|------|
| Maximum AC Charge Power | 11 | Continuous | 25°C | kW |
| Maximum DC Fast Charge Power | 150 | Until 80% SOC | 25°C | kW |
| Taper Charge Power (80-100%) | 50 → 10 | Variable | 25°C | kW |

### 4.3 Power Derating

Power capabilities shall derate based on:
- Temperature: Linear derating below 0°C and above 40°C
- State of Charge: Reduced power below 10% and above 90% SOC
- State of Health: Power reduces proportionally with capacity fade
- Cell Imbalance: 5% power reduction per 50mV maximum cell voltage difference

## 5. Impedance Specifications

### 5.1 DC Resistance
- Pack DC Resistance (DCR) at 25°C: ≤ 80 mΩ
- Maximum DCR increase over life: 50%
- DCR temperature coefficient: -0.5%/°C

### 5.2 AC Impedance
- Impedance at 1 kHz: ≤ 60 mΩ
- Impedance measurement frequency range: 0.1 Hz - 10 kHz

## 6. Efficiency

### 6.1 Charge/Discharge Efficiency
- Round-trip efficiency (SOC 20-80%): ≥ 95%
- Discharge efficiency: ≥ 98%
- Charge efficiency: ≥ 97%

### 6.2 Self-Discharge
- Self-discharge rate at 25°C: ≤ 3% per month
- Self-discharge rate at 40°C: ≤ 5% per month

## 7. Voltage Limits and Protection

### 7.1 Cell Voltage Limits

| Limit Type | Value | Action | Unit |
|------------|-------|--------|------|
| Maximum Charge Voltage | 4.20 | Charge cutoff | V |
| Over-voltage Protection | 4.25 | Contactor open, warning | V |
| Over-voltage Fault | 4.30 | Contactor open, fault | V |
| Minimum Discharge Voltage | 2.80 | Discharge cutoff | V |
| Under-voltage Protection | 2.70 | Contactor open, warning | V |
| Under-voltage Fault | 2.50 | Contactor open, fault | V |

### 7.2 Pack Voltage Limits

| Limit Type | Value | Action | Unit |
|------------|-------|--------|------|
| Maximum Operating Voltage | 420 | Normal operation limit | V |
| Over-voltage Protection | 454 | Contactor open | V |
| Minimum Operating Voltage | 302 | Normal operation limit | V |
| Under-voltage Protection | 270 | Contactor open | V |

## 8. Current Limits

### 8.1 Discharge Current Limits

| Parameter | Value | Unit |
|-----------|-------|------|
| Maximum Continuous Current | 375 | A |
| Peak Current (10s) | 625 | A |
| Over-current Protection | 700 | A |
| Over-current Fault | 800 | A |

### 8.2 Charge Current Limits

| Parameter | Value | Unit |
|-----------|-------|------|
| Maximum Continuous Charge Current | 200 | A |
| Peak Charge Current (10s) | 400 | A |
| Over-current Protection | 450 | A |

## 9. Insulation Requirements

### 9.1 Insulation Resistance
- Minimum insulation resistance (HV+ to chassis): ≥ 100 Ω/V
- Minimum insulation resistance (HV- to chassis): ≥ 100 Ω/V
- Insulation monitoring: Continuous during operation

### 9.2 Isolation Monitoring
- Isolation fault threshold: < 100 Ω/V
- Response time: ≤ 1 second
- Warning indication: Required at 200 Ω/V

## 10. Electromagnetic Compatibility (EMC)

### 10.1 Conducted Emissions
- Compliance with CISPR 25 Class 5

### 10.2 Radiated Emissions
- Compliance with CISPR 25 Class 5

### 10.3 Immunity
- ISO 11452-2: Radiated immunity
- ISO 11452-4: Bulk current injection
- ISO 7637-2: Transient immunity

## 11. Measurement Accuracy Requirements

### 11.1 Voltage Measurement
- Cell voltage accuracy: ±10 mV
- Pack voltage accuracy: ±0.5% of reading
- Resolution: 1 mV

### 11.2 Current Measurement
- Current accuracy: ±0.5% of full scale
- Resolution: 0.1 A
- Measurement range: -500A to +500A

### 11.3 Temperature Measurement
- Temperature accuracy: ±2°C
- Resolution: 0.1°C

## 12. Testing Requirements

### 12.1 Acceptance Testing
- All electrical parameters shall be verified during acceptance testing
- Testing at -10°C, 25°C, and 45°C
- Power capability verification at 10%, 50%, 90% SOC

### 12.2 Type Testing
- Full electrical characterization per ISO 12405-1
- Cycle life testing: 2000 cycles at 80% DOD
- Pulse power characterization per USABC HPPC test

### 12.3 Production Testing
- Voltage verification: 100% of cells and pack
- Insulation resistance: 100% of packs
- Self-discharge: Sample basis (5% of production)
