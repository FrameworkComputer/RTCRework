# RTC Rework (Testing)
** Note that this rework is still in testing, and the files are a release candidate version **

![image](https://github.com/FrameworkComputer/RTCRework/assets/28994301/743a683b-725c-4fce-906b-da8bf186ab0a)

This is a "fake" ML1220 RTC Battery that can be inserted into an 11th Gen Intel Core Framework Laptop Mainboard as a
replacement for a real ML1220.  There is a known issue on 11th Gen where RTC battery voltage dropping below a certain
level can in some scenarios result in the CPU entering a bad state and not booting until the main battery and RTC battery
are cycled.

With this fake RTC Battery, the RTC circuit remains powered from either AC or the main battery at all times,
preventing the CPU from entering the bad state.  Note that since it is not a real battery, if both AC and the main
battery are disconnected, the clock will be reset.  The OS will be able to recover the clock once it connects to a network.
This behavior matches essentially how 12th Gen works with the RTC battery removed, and how 13th Gen and Ryzen 7040 Series work
by default, since we no longer ship with an RTC battery installed.

## Fabrication
The outputs in the outputs directory contain the necessary information to have a fab house like PCBWay or similar fabricate
the PCBs and do SMT and manual assembly.  Note that the PCB must be 2.0mm thick, have ENIG plating, and have edge plating.

## Assembly
1. Strip 3mm from each side of 60mm long, 30 AWG solid wire.
2. Solder one side of the wire to the pad on the top of the PCB that is labelled 17.6V
3. Apply a 10mm diameter disc of kapton tape on the top of the PCB, covering the pad and SMT parts
4. Carefully remove the existing RTC battery from the Mainboard using a SIM eject tool
5. Remove the protective black mylar from the Mainboard to the right of the RTC battery socket
6. Solder the other end of the wire to the point marked in the image below
7. Carefully insert the PCB into the RTC battery socket on the Mainboard
8. Place the black mylar back on the Mainboard

![rtc_rework_assembly](https://github.com/FrameworkComputer/RTCRework/assets/28994301/ef47ba6d-104f-4b66-9648-7e397f705647)

## License
RTC Rework © 2023 by Framework Computer Inc is licensed under CC BY 4.0. To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/
