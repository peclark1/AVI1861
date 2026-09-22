# PLD validation record

Validated from WinCUPL II v1.1.0 project output supplied 2026-09-22.

## Target configuration

Both projects were configured as:

- Device family: ATF22V10C
- Package: 24-TSSOP
- Option: None
- Device mnemonic selected by WinCUPL II: P22V10
- JEDEC output enabled

The original upstream PLD sources retain `DEVICE G22V10;`. WinCUPL II compiled those sources for the selected ATF22V10C project target and emitted JEDEC headers identifying `Device p22v10`.

## U1 / LINE

- Source identity: LINE, revision B, location U1
- Compiler: CUPL(WM) 5.0a, as packaged with WinCUPL II v1.1.0
- Compile result: Normal exit, Error Code = 0
- JEDEC device: p22v10
- JEDEC fuse count: 5828
- JEDEC fuse checksum: C54D
- JEDEC transmit checksum: 4B12
- SHA-256 of supplied JEDEC: `5b716aa3e9a2dcbc9069d18bc5c355d0ff06572d76906989cba2b2870f824a2d`

## U2 / FRAME

- Source identity: FRAME, revision C, location U2
- Compiler: CUPL(WM) 5.0a, as packaged with WinCUPL II v1.1.0
- JEDEC device: p22v10
- JEDEC fuse count: 5828
- JEDEC fuse checksum: 95B1
- JEDEC transmit checksum: DE7B
- SHA-256 of supplied JEDEC: `27ae50b1344311a08d7cbf9dc7968df402f38a6e05c30ee2c95cd7b3a779d455`

The FRAME listing contains the expected upstream FRAME revision C source and terminates with the checksum without compiler warning/error text. The supplied archive's FRAME project file has blank file-name fields, apparently because of how the source was attached to the project, but the generated listing and JEDEC identify FRAME/U2 correctly.

## Source clarification

The current upstream README and Rev A errata specify CD4014 for U3. The older CD4021 wording in the comment block of line.pld is stale documentation.

## Release status

These files establish a clean WinCUPL compile and correct physical PLD target. Before releasing the assembly order, still:

1. Add the exact JEDEC files supplied by the builder to the manufacturing package.
2. Confirm PCBWay programming support for ATF22V10C-10XU using JEDEC input.
3. Perform visual Gerber/placement validation.
4. Select J1 plug-in pin hardware.
