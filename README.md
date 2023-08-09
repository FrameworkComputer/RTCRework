# RTC Rework
![image](https://github.com/FrameworkComputer/RTCRework/assets/28994301/743a683b-725c-4fce-906b-da8bf186ab0a)

## Requesting an RTC Battery Substitute module

If you have an 11th Gen system or Mainboard, you can now [reach out to support](https://framework.kustomer.help/contact/support-request-ryon9uAuq) to request a free RTC Battery Substitute module. 
To make the request process go smoothly, enter the email address that you ordered the 11th Gen product on and/or include photos of the system and Mainboard serial numbers.

Note that there are no constraints making this request other than being an 11th Gen system or Mainboard owner (whether or not you are in warranty). 
We ask that you really make sure you are comfortable with performing soldering on expensive electronics items before performing the installation, 
as we won’t be able to provide advice or support around soldering or provide fixes for failed soldering attempts. 
We also ask that you only make the request if you’ve faced needing to perform a Mainboard reset, as we want to avoid waste.

## Details

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
Steps 1 through 3 can be done by the PCB fab/assembly supplier (we've used PCBWay, but there are many similar ones), while
the remaining steps are done on the specific Framework Laptop.

1. Strip 3mm from each side of 60mm long, 30 AWG solid wire.
2. Solder one side of the wire to the pad on the top of the PCB that is labelled 17.6V
3. Apply a 10mm diameter disc of kapton tape on the top of the PCB, covering the pad and SMT parts
4. Follow the [step by step guide](https://guides.frame.work/Guide/RTC+Battery+Substitution+on+11th+Gen+Intel%C2%AE+Core%E2%84%A2/203) with photos and video for the remaining steps.


![rtc_rework_assembly](https://github.com/FrameworkComputer/RTCRework/assets/28994301/ef47ba6d-104f-4b66-9648-7e397f705647)

## License
RTC Rework © 2023 by Framework Computer Inc is licensed under CC BY 4.0. To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/
