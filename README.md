# 🏭 Automatic Bottle Filling Machine

Industrial automation project: **Siemens S7-1200 PLC** + **TP900 Comfort HMI**

---

## 📋 Overview

Automated bottle filling system with conveyor control, liquid pump, filling valve, bottle counting, and professional HMI interface with multi-level user authentication.

## 🔧 Hardware

| Component | Model |
|-----------|-------|
| PLC | S7-1200 CPU 1214C DC/DC/DC |
| HMI | TP900 Comfort 9" Touch |
| Software | TIA Portal V14 |
| Network | PROFINET |

## 📥 I/O List

**Inputs:**
| Address | Description |
|---------|-------------|
| %I0.0 | Start Button |
| %I0.1 | Stop Button |
| %I0.2 | Emergency Stop |
| %I0.3 | Proximity Sensor |
| %I0.4 | Level Sensor |
| %I0.5 | Auto/Manual Switch |
| %I0.6 | Tank Low Level |
| %I0.7 | Reset Button |

**Outputs:**
| Address | Description |
|---------|-------------|
| %Q0.0 | Conveyor Motor |
| %Q0.1 | Filling Valve |
| %Q0.2-0.5 | Indicator Lights + Buzzer |
| %Q0.6 | Yellow Light (Filling) |
| %Q0.7 | Pump Motor |

## 🔄 Process
START → Conveyor ON → Bottle Detected → Conveyor STOP
→ Filling (3 sec) → Counter +1 → Conveyor ON → Repeat
→ Target Reached → Machine STOPS

## 🖥️ HMI Screens

| # | Screen | Function |
|---|--------|----------|
| 1 | Main | Machine view + Status + Controls |
| 2 | Menu | Navigation  |
| 3 | Manual | Individual equipment control |
| 4 | Settings | Production target + Counter reset |
| 5 | Alarms | Active alarms + Reset |
| 6 | Trends | Production graphs |
| 7 | Login | User/Admin authentication |

**Access:** User=1111, Admin=9999

## 📁 PLC Program

**OB1 (Ladder - 20 Networks):**
| # | Function |
|---|----------|
| 1 | Machine Start/Stop |
| 2-3 | Auto/Manual Mode |
| 4-5 | Conveyor + Pump Motor |
| 6 | Bottle Detection |
| 7 | Filling Control |
| 8 | TON Timer (3s) |
| 9 | Counter Reset + Production Target |
| 10 | Valve + Yellow Light |
| 11-12 | Alarms |
| 13-16 | Lights + Buzzer |
| 17 | Login System (FC1 Call) |

**FC1 (SCL):** Login system with CASE statement

## 🚀 How to Use

1. Open TIA Portal V14
2. Retrieve archive (`.zap14`)
3. Compile + Download to PLCSIM
4. Start HMI Runtime
5. Login: `9999` → Press START

## 👤 Author

**[Mouhcine_elassar]** - Technicien automamaticien
