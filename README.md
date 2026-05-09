# 4-in-1 Quadcopter ESC (STM32F407 + DRV8323RS)

**High-performance 4-in-1 Electronic Speed Controller** for BLDC motors in quadcopters/drones.

![PCB Layout](docs/pcb/PCB_3D_top_view_8-05-2026.png)
![Schematic Preview](docs/schematics/gate_drivers_schematic_8-05-2026.png)

## Specifications
- **Battery**: 4S LiPo (5.2Ah 35C/60C)
- **Motor**: 1400KV BLDC, ~7A max efficient current per motor
- **MOSFET**: MCG4D8N04YHE3-TP (x12 for 4-in-1)
- **Gate Driver**: DRV8323RS (x4)
- **MCU**: STM32F407VET6
- **Layout**: 4-in-1 ESC board
- **Firmware**: Custom (in development) — supports [target protocol, e.g., DShot, PWM]

## Features
- 4 independent 3-phase half-bridges
- High-current power stage optimized for 4S
- SPI / UART interface for configuration and telemetry
- Current sensing & protection

## Project Status
- Schematic V2 complete (multi-motor sheets)
- PCB layout in progress (see attached files)
- Firmware skeleton in development

## Repository Contents
- `project files (kicad)/` — KiCad 8+ schematic + PCB files
- `docs/` — Schematics PDF, BOM, images

## Quick Start
1. Clone repo
2. Open `hardware/ESC_4in1.kicad_pro` in KiCad
3. Review power stage, gate driver, and MCU sections
4. Generate Gerbers for manufacturing

## Firmware
(Instructions coming soon — STM32CubeIDE / PlatformIO)

## Contributing
Contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) (create later).

## License
MIT License — see [LICENSE](LICENSE) file.

---

## Roadmap & Future Improvements

### High Priority
- **Board Miniaturization**
  - Current dimensions: **108.6 × 77.5 mm** (4 layers)
  - Target: Reduce to **≤ 70 × 70 mm** or closer to standard 30.5×30.5mm / 40×40mm mounting patterns while maintaining proper thermal performance and clearance.
  - Optimize component placement and routing
  - Evaluate moving to 6-layer PCB if it enables significant size reduction
  - Improve power plane design and thermal vias under MOSFETs

- **Firmware Development**
  - Implement full BLDC FOC / Trapezoidal control using STM32F407
  - Support DShot600 / DShot1200 protocols
  - Current sensing and over-current protection
  - Telemetry (voltage, current, temperature, RPM)
  - DRV8323RS configuration via SPI
  - Sensorless startup and BEMF detection tuning
  - PID tuning for smooth throttle response

### Medium Priority
- Add onboard 5V / 3.3V BEC with better filtering
- Improve EMI/EMC performance (snubbers, capacitor placement)
- Add status LEDs and debugging interfaces (SWD + UART)
- Thermal simulation and real-world heat testing
- Input protection (TVS diodes, reverse polarity)
- Create a configurable GUI tool (Python / Qt) for tuning parameters

### Long Term
- Support higher current motors (optimize MOSFET cooling)
- 6S battery compatibility
- Open-source configurator tool
- Flight testing on a test quadcopter
- Documentation for assembly and calibration
