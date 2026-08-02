# USB 3.1 Gen 1 to Gigabit Ethernet Interface

This project is a hardware implementation of a USB 3.1 Gen 1 to Gigabit Ethernet adapter designed in KiCad. It is based on the Microchip LAN7801 USB-to-Ethernet controller and the KSZ9031RNX Gigabit Ethernet PHY.

The goal of this project was to gain practical experience in designing a high-speed PCB while following signal integrity, power integrity, and layout guidelines required for USB 3.1 and Gigabit Ethernet interfaces.

---

# Overview

The LAN7801 acts as the USB 3.1 Gen 1 bridge and Ethernet MAC, converting 5 Gbps USB SuperSpeed data into a 125 MHz RGMII interface. The KSZ9031RNX then converts the RGMII data into standard Gigabit Ethernet signals that are transmitted through the RJ45 MagJack.

The design uses dedicated 3.3V and 1.2V power rails. Instead of using an external 1.2V regulator, the KSZ9031RNX's integrated LDO controller is used with a DMG2301L P-channel MOSFET to generate the PHY core supply, reducing the overall component count.

A 25 MHz ABM8G crystal provides the reference clock for both devices.

---

# PCB Layout

### Top Layer

![Top Layer](Images/top_layer.png)

---

### Bottom Layer

![Bottom Layer](Images/bottom_layer.png)

---

### 3D View

![3D View](Images/3d_view.png)

---

# Hardware Block Diagram

![Block Diagram](Images/block_diagram.png)

The USB Type-A connector interfaces with the LAN7801 controller. The controller communicates with the KSZ9031RNX Gigabit PHY over the RGMII interface, while MDIO/MDC is used for PHY configuration. The PHY then drives the RJ45 MagJack to provide a standard Gigabit Ethernet connection.

---

# Design Approach

The project started by studying the LAN7801 and KSZ9031RNX datasheets along with the manufacturer's reference designs to understand the required interfaces, power supplies, clocking, and layout recommendations.

After completing the schematic, component placement was planned carefully to keep high-speed signal paths as short as possible. The USB controller was placed close to the USB connector, while the Ethernet PHY was positioned near the RJ45 MagJack to minimize RGMII routing.

During PCB layout, the main focus was maintaining signal integrity by following controlled impedance routing, differential pair routing, length matching, proper grounding, and good decoupling practices.

---

# Main Components

| Component | Description |
|----------|-------------|
| LAN7801 | USB 3.1 Gen 1 to Gigabit Ethernet Controller |
| KSZ9031RNX | Gigabit Ethernet PHY |
| ABM8G | 25 MHz Crystal Oscillator |
| DMG2301L | P-Channel MOSFET |
| RJ45 MagJack | Gigabit Ethernet Connector |
| USB Type-A Connector | USB SuperSpeed Interface |

---

# PCB Design Highlights

- 4-layer PCB stack-up
- USB 3.1 SuperSpeed differential pair routing
- 125 MHz RGMII interface routing
- Controlled impedance traces
- Differential pair length matching
- Continuous ground plane
- Proper decoupling capacitor placement
- ESD protection for external interfaces
- Power integrity considerations

---

# Design Challenges

Some of the key challenges while designing this PCB were:

- Routing USB SuperSpeed differential pairs while maintaining impedance.
- Length matching the RGMII interface.
- Placing decoupling capacitors close to the IC power pins.
- Maintaining clean return current paths using continuous ground planes.
- Planning the component placement to minimize high-speed routing complexity.
- Following the layout recommendations provided in the component datasheets.

---

# Software Used

- KiCad
- Saturn PCB Toolkit
- Pspice

---

# Future Improvements

- Generate complete fabrication outputs (Gerber, Drill, BOM and Pick & Place files).
- Perform impedance verification using PCB stack-up calculations.
- Prototype and validate the hardware with functional testing.
- Perform USB and Ethernet compliance testing.

---

# Author

**Ayush Shukla**

B.Tech Electronics & Telecommunication Engineering
