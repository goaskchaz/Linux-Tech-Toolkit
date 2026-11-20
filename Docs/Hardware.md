# Hardware Inventory and Interfaces

**Status:** Pending laptop inspection

## Host laptop
| Property | Value |
|---|---|
| Manufacturer | HP |
| Model | Pavilion — exact model TBD |
| Processor / architecture | TBD |
| RAM | TBD |
| Internal storage | TBD |
| Firmware (BIOS/UEFI) | TBD |
| Ethernet / Wi-Fi chipset | TBD |
| USB ports | TBD |
| Linux distribution | TBD after live-USB test |

## Recommended adapters
| Interface | Purpose | Caution |
|---|---|---|
| USB-to-SATA / powered disk dock | HDD/SSD service | Use adequate external power for drives that require it |
| USB-to-UART (3.3 V / 5 V) | MCU serial console | Match logic voltage; never connect to mains/PLC field voltage |
| USB-to-RS232 | Legacy serial devices | RS232 is not TTL UART |
| Isolated USB-to-RS485 | Modbus RTU / industrial devices | Confirm wiring, termination, ground and isolation |
| USB Ethernet | Independent network test interface | Test supported Linux chipset |
| USB logic analyzer | Digital protocol inspection | Respect input voltage limits |
| SWD/JTAG debug probe | Embedded debugging | Confirm target voltage and pinout |
| RTL-SDR (optional) | RF experiments | Observe local transmission rules |
| Powered USB hub | Multiple peripherals | Avoid overloading laptop USB ports |

## Pre-installation checks
1. Record hardware model, RAM, storage and firmware settings.
2. Back up any data that must be retained.
3. Test live Linux boot, keyboard, display, Wi-Fi, Ethernet and USB.
4. Confirm external storage and serial adapters are detected.
5. Only then decide whether to replace the existing operating system.
