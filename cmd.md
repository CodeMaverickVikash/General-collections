How can you retrieve system information using the "wmic" command?
General syntax - wmic [alias] [where] [verb] [format]
To view the complete list of aliases, type - wmic /?
to get all info about alias/hardware - wmic MEMORYCHIP list full

General used alias:
memphysical - maxcapacity, memorydevices
memorychip - memorytype, smbiosmemorytype, speed
cpu
bios - serialnumber
