# Windows WMIC Command Reference

Retrieve system information on Windows using the `wmic` command-line utility.

## General Syntax
```cmd
wmic [alias] [where] [verb] [format]
```

## Quick Reference Commands

- **View complete list of aliases:**
  ```cmd
  wmic /?
  ```

- **Get all info about alias / hardware:**
  ```cmd
  wmic MEMORYCHIP list full
  ```

## Commonly Used Aliases & Key Properties

| Alias | Description | Common Properties |
| :--- | :--- | :--- |
| `memphysical` | Physical memory configuration | `maxcapacity`, `memorydevices` |
| `memorychip` | Installed RAM modules | `memorytype`, `smbiosmemorytype`, `speed` |
| `cpu` | Processor information | Core count, clock speed, name |
| `bios` | BIOS firmware details | `serialnumber`, version |
