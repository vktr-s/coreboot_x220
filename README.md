# coreboot_x220
Configuration Coreboot 4.19 for ThinkPad x220 i7-2640m
------

```
General
      Compiler to use (GCC) --->
      Option backend to use (Use CMOS for configuration values) --->
  [*] Compress ramstage with LZMA
  [*] Include coreboot .config file into the ROM image
  [*] Allow use of binary-only repository
  [*] Add a bootsplash image
      (/home/nyancat/Code/coreboot_thinkpad_x220/bootsplash.jpg) Bootsplash path and filename

Mainboard
  *** Important: Run 'make distclean' before switching boards ***
  Mainboard vendor (Lenovo) --->
  Mainboard model (ThinkPad X220) --->
  ROM chip size (8192 KB (8 MB)) --->
  (0x100000) Size of CBFS filesystem in ROM

Chipset
      *** SoC ***
      *** CPU ***
  [*] Enable VMX for virtualization
  [*] Set IA32_FEATURE_CONTROL lock bit
      Include CPU microcode in CBFS (Generate from tree) --->

      *** Northbridge ***
  [*] Use native raminit
  [*] Ignore vendor programmed fuses that limit max. DRAM frequency

      *** Southbridge ***

      *** Super I/O ***
      *** Embedded Controllers ***

      *** Intel Firmware ***
  [*] Add Intel descriptor.bin file
      (3rdparty/blobs/mainboard/$(MAINBOARDDIR)/descriptor.bin) Path and filename
  [*] Add Intel ME/TXE firmware
      (3rdparty/blobs/mainboard/$(MAINBOARDDIR)/me.bin) Path to management engine firmware
  [*] Allows HOST/CPU read access to ME region
  [*] Add gigabit ethernet firmware
      (3rdparty/blobs/mainboard/$(MAINBOARDDIR)/gbe.bin) Path to gigabit ethernet

Devices
      Graphics initialization (Run VGA Option ROMs) --->
      (0) Graphics initialization delay in ms
  [*] Use onboard VGA as primary video device
  [*] Re-run VGA Option ROMs on S3 resume
  [*] Load Option ROMs on PCI devices
      Option ROM execution type (Native mode) --->
  [*] Allow coreboot to set optional PCI bus master bits
  -*-   PCI bridges
  [*]   Any devices
  -*- Enable PCIe Common Clock
  -*- Enable PCIe ASPM
  [*] Enable PCIe Clock Power Management
  [*] Enable PCIe ASPM L1 SubState
  [*] Enable PCIe Hotplug Support
  [*] Add a VGA BIOS image
      (3rdparty/blobs/mainboard/$(MAINBOARDDIR)/vgabios.bin) VGA BIOS path and filename
      (8086,0126) VGA device PCI IDs
  [*] Add a Video Bios Table (VBT) binary to CBFS
      (src/mainboard/$(MAINBOARDDIR)/variants/x220/data.vbt) VBT binary path and filename

Generic Drivers
  [*] PS/2 keyboard init
  [*] Support Intel PCI-e WiFi adapters

Security

Console
  [*] Squelch AP CPUs from early console
  [*] Show POST codes on the debug console

System Tables
  [*] Generate SMBIOS tables

Payload
      Add a payload (SeaBIOS) --->
      SeaBIOS version (1.16.0) --->
      (3000) PS/2 keyboard controller initialization timeout (milliseconds)
  [*] Hardware init during option ROM execution
      Payload compression algorithm (Use LZMA compression for payloads) --->
  [*] Use LZMA compression for secondary payloads
      Secondary Payloads --->
        [ ] Load coreinfo as a secondary payload
        [ ] Load Memtest86+ as a secondary payloada
        [ ] Load nvramcui as a secondary payload
        [ ] Load tint as a secondary payload

Debugging
```
