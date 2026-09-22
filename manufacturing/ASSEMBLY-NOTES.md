# AVI1861 PCBWay Assembly Notes

Source design: upstream `dmadole/AVI1861`, source commit `531d042c240e8aba471a556550ac4b1128f28a5d`.

## Assembly scope

PCBWay should assemble the SMT components C1, C2 and U1-U6 on the top side.

**J1 is DNI / do not install.** The 24-pin CDP1861-compatible plug-in interface will be installed manually after SMT assembly so that pin geometry can be chosen specifically for reliable insertion into a quality machined-pin DIP socket.

## Programmable logic

U1 and U2 are Microchip `ATF22V10C-10XU` TSSOP-24 PLDs.

- U1 = LINE
- U2 = FRAME

Both must be programmed **before SMT assembly**. PCBWay should confirm that its programming service supports this exact Microchip device and JEDEC programming files before the order is released.

The repository currently contains the authoritative CUPL-style PLD source files under `pld/`. Validated JEDEC files will be added separately; do not program U1/U2 from an unverified conversion.

## U3 shift-register clarification

Use **CD4014B**, specifically TI `CD4014BPWR`.

The upstream README explicitly states that the revised AVI1861 uses a CD4014 because its parallel load is synchronous with the clock. The upstream Rev A errata likewise says the schematic/silkscreen reference to CDP4021 was incorrect and that the part should be CD4014.

The comments near the top of `pld/line.pld` still say CD4021. Those comments are inconsistent with the README, errata, and current schematic value `4014`; treat them as stale documentation, not as the BOM requirement.

## U4 counter

Use **74HC4040**, TI `SN74HC4040PWR`. Upstream revision B1 specifically changes the recommendation from CD4040 to 74HC4040 based on testing.

## Fabrication/placement

All SMT placements are on the top side. Use the generated Gerbers, Excellon drill data, and `AVI1861-pos.csv` from the matching manufacturing workflow artifact.

## Release status

**NOT YET RELEASED FOR MANUFACTURE.** Remaining release gates:

1. Generate and independently validate U1/U2 JEDEC files for ATF22V10C-10XU.
2. Confirm PCBWay can program that exact TSSOP-24 device from JEDEC.
3. Verify Gerber/drill layer set and board dimensions visually.
4. Verify centroid rotations against the PCB/silkscreen.
5. Select the exact 24-pin round/machined plug-in pin solution for J1.
