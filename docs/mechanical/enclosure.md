# Enclosure Design

## Overview

The enclosure provides physical protection, structural support, and environmental sealing for all [battery modules](../core/battery-modules.md) and electrical components.

## Design Specifications

### Dimensions
- **Length**: 1200 mm
- **Width**: 800 mm  
- **Height**: 150 mm
- **Weight**: 8 kg (empty enclosure)

### Materials
- **Main Housing**: 6061-T6 aluminum alloy (3mm wall thickness)
- **Base Plate**: 5mm aluminum with reinforcement ribs
- **Cover**: 2.5mm aluminum with rubber gasket
- **Mounting Brackets**: Steel, powder-coated

## Internal Layout

### Module Arrangement
- 24x [battery modules](../core/battery-modules.md) in 2 rows of 12
- Fire-resistant barriers between module groups
- Thermal interface pads to base plate
- Compression foam for vibration damping

### Electrical Routing
- [Power distribution](../electrical/power-distribution.md) bus bars along centerline
- [BMS](../core/bms.md) wiring harness routed along sidewall
- Service disconnect accessible from top
- Cable glands for external connections (4x M25)

### Thermal Integration
- Base plate acts as [cooling system](thermal-management.md) interface
- Coolant channels bonded to underside
- Thermal paste between cells and aluminum module holders
- Air gaps minimized for heat transfer

## Environmental Protection

### Ingress Protection
- **Rating**: IP67
- **Dust**: Complete protection against dust ingress
- **Water**: Protected against temporary immersion (1m for 30 minutes)
- **Gasket**: Closed-cell silicone rubber, continuous seal
- **Vent**: Gore-Tex membrane for pressure equalization

### Corrosion Resistance
- Aluminum components anodized (Type II, 10-25 microns)
- Steel hardware zinc-plated
- Dissimilar metal contact avoided or isolated
- Drainage holes at low points

## Structural Performance

### Crash Protection
- Perimeter crush zones designed to deform before cell damage
- Module mounting designed to prevent shifting
- Integrated into vehicle floor structure
- Side impact protection: 50 km/h pole test compliant

### Vibration and Shock
- Testing per ISO 16750-3 automotive standards
- Module mounting: 4-point compression with isolation
- Natural frequency >50 Hz to avoid resonance
- Shock testing: 40G half-sine pulse, 11ms duration

## Mounting to Vehicle

- 8x M10 bolts to vehicle floor pan
- Elastomeric isolators for vibration isolation
- Grounding strap for electrical safety
- Alignment pins for precise positioning

## Serviceability

### Access
- Top cover removable with 20x M6 bolts
- Service disconnect accessible without cover removal
- [BMS](../core/bms.md) diagnostic connector external
- Module replacement possible without removing enclosure

### Maintenance
- Gasket replacement recommended every 5 years
- Connector inspection at 100k km
- Coolant system service per [thermal management](thermal-management.md) schedule
- Torque check on all HV connections annually

## Safety Features

Integration with [Safety Systems](../electrical/safety-systems.md):
- High-voltage warning labels (ISO 7010-W012)
- Service disconnect lockout provision
- First responder cut zone markings
- No exposed HV terminals when cover installed

## Related Documents

- [Battery Modules](../core/battery-modules.md) - Internal components
- [Battery Management System](../core/bms.md) - Electronic components
- [Power Distribution](../electrical/power-distribution.md) - Electrical connections
- [Safety Systems](../electrical/safety-systems.md) - Protection features
- [Thermal Management](thermal-management.md) - Cooling integration
- [Connectors](connectors.md) - External interface details
