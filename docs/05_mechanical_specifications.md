# Battery Mechanical Design Specifications

## Document Information
- **Document ID**: BAT-MECH-005
- **Version**: 1.0
- **Date**: 2025-11-04
- **Author**: Mechanical Engineering Team
- **Status**: Draft

## 1. Introduction

This document defines the mechanical design specifications, structural requirements, and packaging constraints for the automotive battery pack assembly.

## 2. Physical Dimensions and Mass

### 2.1 Overall Pack Dimensions

| Parameter | Value | Tolerance | Unit |
|-----------|-------|-----------|------|
| Length | 1850 | ±10 | mm |
| Width | 1450 | ±10 | mm |
| Height | 150 | ±5 | mm |
| Volume | 402 | - | liters |
| Mass (total) | 485 | ±15 | kg |
| Mass (cells only) | 320 | - | kg |

### 2.2 Module Dimensions

| Parameter | Value | Tolerance | Unit |
|-----------|-------|-----------|------|
| Length | 450 | ±5 | mm |
| Width | 280 | ±5 | mm |
| Height | 110 | ±3 | mm |
| Mass per module | 26 | ±1 | kg |
| Number of modules | 12 | - | - |

### 2.3 Cell Dimensions

| Parameter | Value | Tolerance | Unit |
|-----------|-------|-----------|------|
| Length | 148 | ±0.5 | mm |
| Width | 91 | ±0.5 | mm |
| Height | 105 | ±0.5 | mm |
| Mass per cell | 1.48 | ±0.05 | kg |
| Cell volume | 1.42 | - | liters |

### 2.4 Center of Gravity

| Parameter | Value | Reference | Unit |
|-----------|-------|-----------|------|
| Longitudinal CG | 925 | From front edge | mm |
| Lateral CG | 725 | From left edge | mm |
| Vertical CG | 75 | From bottom | mm |

## 3. Structural Requirements

### 3.1 Static Load Requirements

| Load Case | Direction | Load | Safety Factor |
|-----------|-----------|------|---------------|
| Self-weight support | Vertical (Z) | 1g | 3.0 |
| Cornering | Lateral (Y) | 1.5g | 2.0 |
| Braking | Longitudinal (X) | 2.0g | 2.0 |
| Combined loading | X+Y+Z | 2.5g | 1.5 |

### 3.2 Dynamic Load Requirements

| Load Case | Value | Duration | Safety Factor |
|-----------|-------|----------|---------------|
| Shock loading | 30g | 5 ms | 1.5 |
| Vibration (swept sine) | 20g | 10-200 Hz | 1.5 |
| Random vibration | 10g RMS | Per ISO 16750 | 1.5 |

### 3.3 Structural Integrity

- No permanent deformation under normal operating loads
- No structural failure under ultimate loads (limit load × safety factor)
- Maximum deflection under 1g static load: 5 mm
- First natural frequency: > 50 Hz
- No resonance frequencies in range 20-100 Hz

## 4. Materials Specifications

### 4.1 Pack Housing/Enclosure

| Component | Material | Standard | Properties |
|-----------|----------|----------|------------|
| Bottom plate | Aluminum 6061-T6 | ASTM B209 | Thickness: 3 mm |
| Upper cover | Aluminum 6061-T6 | ASTM B209 | Thickness: 2 mm |
| Side walls | Aluminum extrusion 6063-T5 | ASTM B221 | Wall: 3 mm |
| Mounting brackets | Steel A36 | ASTM A36 | Thickness: 5 mm |

**Material Properties:**
- Yield Strength: 240 MPa (Al 6061-T6)
- Ultimate Tensile Strength: 290 MPa (Al 6061-T6)
- Density: 2700 kg/m³ (Aluminum)
- Thermal Expansion: 23.6 × 10⁻⁶ /°C

### 4.2 Module Structure

| Component | Material | Standard |
|-----------|----------|----------|
| Module frame | Aluminum 6063-T5 | ASTM B221 |
| Compression plates | Aluminum 5052-H32 | ASTM B209 |
| End plates | Steel, powder coated | ASTM A366 |
| Fasteners | Stainless steel 304 | ASTM F593 |

### 4.3 Sealing and Gaskets

| Component | Material | Standard | Properties |
|-----------|----------|----------|------------|
| Main seal | EPDM rubber | ASTM D2000 | Shore A hardness: 60-70 |
| Gasket | Silicone foam | MIL-P-21929 | Compression: 25% |
| O-rings | FKM (Viton) | AS568 | High temperature resistant |

### 4.4 Thermal Management Materials

| Component | Material | Properties |
|-----------|----------|------------|
| Cooling plates | Aluminum 3003 | Thermal conductivity: 160 W/mK |
| Thermal interface | Gap filler pad | Thermal conductivity: 3 W/mK |
| Thermal barriers | Mica composite | Fire resistant, thermal insulation |

## 5. Cell Retention and Compression

### 5.1 Compression Requirements

| Parameter | Value | Unit |
|-----------|-------|------|
| Compression force per cell | 500 | N |
| Compression uniformity | ±10% | - |
| Compression method | Spring-loaded plates | - |
| Spring rate | 50 | N/mm |
| Spring travel | 10 | mm |

### 5.2 Cell Retention Method

- Compression plates at module ends
- Spring stacks for compression force
- Side guides for lateral constraint
- Bottom support for vertical support
- Expansion allowance: ±2mm per cell

### 5.3 Swelling Accommodation

- Cell swelling over life: 3% typical, 5% maximum
- Module expansion allowance: 15 mm
- Compression force maintenance: 400-600 N per cell over life

## 6. Fastening and Assembly

### 6.1 Fastener Specifications

| Application | Type | Size | Material | Torque |
|-------------|------|------|----------|--------|
| Cover to housing | Bolt | M6 | SS 304 | 8 Nm |
| Module to structure | Bolt | M8 | SS 304 | 20 Nm |
| Busbar connections | Bolt | M6 | Copper plated | 6 Nm |
| Cooling plate | Bolt | M5 | SS 304 | 5 Nm |
| Ground connections | Bolt | M6 | SS 304 | 8 Nm |

### 6.2 Fastener Retention

- Thread locking compound: Loctite 243 (medium strength)
- Critical fasteners: Safety wire or lock wire
- Vibration resistance: Prevailing torque nuts or Nord-Lock washers
- Inspection: Torque verification at assembly

### 6.3 Assembly Sequence

1. Install cooling plates in bottom housing
2. Apply thermal interface material to cooling plates
3. Install cell modules onto cooling plates
4. Connect busbars between modules
5. Install slave BMS boards
6. Connect temperature sensors
7. Install master BMS and contactor assembly
8. Seal and install upper cover
9. Pressure test seal integrity
10. Electrical function check

## 7. Sealing and Ingress Protection

### 7.1 IP Rating

- Ingress Protection Rating: IP67
- Dust Protection: Complete protection (IP6X)
- Water Protection: Protected against immersion up to 1m for 30 min (IPX7)

### 7.2 Seal Design

| Feature | Specification |
|---------|--------------|
| Seal type | Compression seal |
| Seal width | 10 mm |
| Seal compression | 25-30% |
| Seal path | Continuous around perimeter |
| Seal groove depth | 3 mm |
| Seal groove width | 8 mm |

### 7.3 Penetration Sealing

- Electrical connectors: IP67 rated connectors
- Coolant ports: O-ring sealed fittings
- Pressure relief valve: Sealed and vented externally
- Cable glands: IP67 rated, strain relief

### 7.4 Vent System

- Vent valve type: Gore-Tex membrane vent
- Vent flow rate: 0.5 L/min at 70 mbar
- Vent location: Highest point of pack
- Vent direction: Downward, away from occupants
- Particulate filtering: 0.2 μm membrane

## 8. Thermal Barriers and Fire Protection

### 8.1 Thermal Barrier Requirements

| Parameter | Specification |
|-----------|--------------|
| Material | Mica-based composite or ceramic |
| Thickness | 3 mm minimum |
| Location | Between modules |
| Thermal resistance | Delay propagation ≥5 min |
| Temperature rating | 1000°C |

### 8.2 Fire Protection

- Cell-to-cell barriers within modules
- Module-to-module barriers in pack
- Flame retardant materials (UL94 V-0 rating)
- Self-extinguishing design
- Directed gas venting

## 9. Mounting and Integration

### 9.1 Vehicle Mounting

| Parameter | Specification |
|-----------|--------------|
| Mounting points | 8 locations on pack perimeter |
| Mounting type | Rubber isolated bushings |
| Bushing stiffness | 500 N/mm (vertical), 1000 N/mm (lateral) |
| Load path | Through frame structure |
| Ground connection | 2 locations, low impedance path |

### 9.2 Mounting Interface

- Mounting bolt pattern: Standard vehicle floor pan
- Vertical clearance required: 200 mm minimum
- Access requirements: Removable from below
- Alignment features: Dowel pins (4 locations)

### 9.3 Crash Isolation

- Deformation zones: Outside pack perimeter
- Crush cans: Integrated in vehicle structure
- No direct load path through cells
- Mounting designed to shear in extreme crash

## 10. Electrical Connections

### 10.1 High Voltage Connectors

| Connector | Type | Rating | Features |
|-----------|------|--------|----------|
| HV+ main | 2-pole | 450V, 500A | Manual service disconnect |
| HV- main | 2-pole | 450V, 500A | Interlock integrated |
| Charge inlet | 2-pole | 450V, 400A | DC and AC compatible |

### 10.2 Low Voltage Connections

| Connection | Type | Rating | Purpose |
|------------|------|--------|---------|
| CAN bus | 4-pin | 12V | Vehicle communication |
| Auxiliary power | 2-pin | 12V, 5A | BMS power supply |
| Interlock circuit | 2-pin | 12V, 1A | Safety interlock |
| Cooling control | 6-pin | 12V | Pump/valve control |

### 10.3 Service Disconnect

- Type: Manual disconnect plug
- Location: Accessible without tools
- Interlock: Integrated in connector
- Indication: Visual indicator of connection state
- Force to disconnect: 50-100 N

## 11. Cooling System Integration

### 11.1 Coolant Ports

| Parameter | Specification |
|-----------|--------------|
| Port size | 16 mm (5/8") |
| Port type | Quick-connect, push-to-connect |
| Number of ports | 2 (inlet/outlet) |
| Material | Aluminum with EPDM seal |
| Flow direction | Marked on connector |

### 11.2 Cooling Plate Design

| Parameter | Specification |
|-----------|--------------|
| Material | Aluminum 3003 |
| Channel depth | 5 mm |
| Channel width | 8 mm |
| Wall thickness | 2 mm |
| Surface finish | Smooth, anodized |
| Contact area | 80% of cell bottom |

## 12. Cable Management

### 12.1 Internal Wiring

- High voltage busbars: Copper, insulated, 50 mm²
- Low voltage wiring: Stranded copper, 1-2.5 mm²
- Wire routing: Protected channels, no sharp edges
- Wire retention: Cable ties every 100 mm
- Color coding: Per IEC 60446

### 12.2 Busbar Design

| Parameter | Specification |
|-----------|--------------|
| Material | Copper alloy C11000 |
| Thickness | 3 mm |
| Width | 50 mm |
| Current capacity | 500A continuous |
| Insulation | Polyimide tape, 0.2 mm |
| Voltage rating | 1000V |

## 13. Labeling and Identification

### 13.1 Required Labels

- High voltage warning labels (ISO 7010-W012)
- Battery specification label (capacity, voltage, weight)
- Serial number and manufacturing date
- QR code for traceability
- Lifting points marking
- Service disconnect location
- Emergency response information

### 13.2 Label Requirements

- Material: Polyester with UV protection
- Adhesion: Permanent, high temperature resistant
- Legibility: Maintained for 10 years
- Language: English and local language
- Color: Per ISO 7010 standards

## 14. Environmental Protection

### 14.1 Corrosion Protection

- Aluminum parts: Anodized or powder coated
- Steel parts: Zinc plated or powder coated
- Fasteners: Stainless steel or zinc-nickel plated
- Busbars: Nickel plated copper
- Salt spray resistance: 1000 hours per ASTM B117

### 14.2 UV Protection

- Exterior components: UV stabilized materials
- Cables: UV resistant jacket
- Seals: UV resistant compounds
- Labels: UV protected printing

## 15. Testing and Validation

### 15.1 Structural Testing

- Static load test: 3g vertical, 2g lateral/longitudinal
- Fatigue test: 100,000 cycles equivalent to 200,000 km
- Shock test: 30g, 5ms half-sine pulse
- Vibration test: ISO 16750-3, 10-200 Hz sweep
- Modal analysis: Natural frequency identification

### 15.2 Environmental Testing

- IP67 verification: Water immersion test
- Pressure test: Leak detection at 20 mbar
- Temperature cycling: -40°C to +80°C, 100 cycles
- Humidity test: 95% RH at 40°C, 48 hours
- Salt spray test: 1000 hours per ASTM B117

### 15.3 Crash Testing

- Frontal impact: 50 km/h barrier
- Side impact: 50 km/h pole
- Rear impact: 40 km/h barrier
- Rollover simulation: Static loading
- Crush resistance: 200 kN top load

### 15.4 Functional Testing

- Assembly torque verification: 100% of fasteners
- Leak test: 100% of packs
- Dimensional inspection: First article and sampling
- Weight verification: 100% of packs
- Electrical connection resistance: Critical joints

## 16. Maintenance and Service

### 16.1 Serviceable Components

- Upper cover: Removable with hand tools
- Cooling system: Drainable and fillable
- HV connectors: Field replaceable
- Fuses: Accessible without disassembly
- Service disconnect: User accessible

### 16.2 Service Intervals

- Visual inspection: Every 12 months
- Cooling system service: Every 24 months
- Seal inspection: Every 24 months
- Mounting torque check: Every 24 months or 50,000 km
- Major service: Every 100,000 km

### 16.3 Special Tools Required

- Torque wrench (5-25 Nm range)
- Insulation resistance meter
- HV safety equipment (gloves, multimeter)
- Coolant filling equipment
- Lifting fixture (for pack removal)

## 17. Quality Requirements

### 17.1 Manufacturing Tolerances

- Dimensional tolerances: Per ISO 2768-m (medium)
- Flatness of sealing surfaces: 0.5 mm per meter
- Parallelism of mounting faces: 0.3 mm
- Surface finish: Ra 6.3 μm for sealing surfaces

### 17.2 Inspection Requirements

- First article inspection: 100% of features
- Production inspection: Per sampling plan AQL 1.0
- Critical dimensions: 100% inspection
- Non-destructive testing: X-ray for critical joints

### 17.3 Traceability

- Component level: Cell date codes, module serial numbers
- Assembly level: Pack serial number, build date
- Batch tracking: Material batch numbers recorded
- Retention: Records maintained for 15 years
