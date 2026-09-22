# AVI1861 Manufacturing Package

This directory contains manufacturing and assembly files generated from the
AVI1861 KiCad source for prototype fabrication/assembly.

## Source revision

- Upstream: `dmadole/AVI1861`
- Source commit: `531d042c240e8aba471a556550ac4b1128f28a5d`
- Fork: `peclark1/AVI1861`
- Working branch: `pcbway-manufacturing`

## Goal

Prepare a reproducible PCBWay-ready package while leaving the upstream
electrical design unchanged.

Planned deliverables:

- Gerber fabrication files
- Excellon drill files
- Pick-and-place / centroid data
- Assembly BOM with exact manufacturer part numbers
- PLD programming files for LINE (U1) and FRAME (U2)
- Assembly notes, including the 24-pin CDP1861-compatible plug-in interface
- Manufacturing validation notes

Generated manufacturing files in this fork are not supplied or endorsed by
the upstream AVI1861 author unless explicitly stated otherwise.

## Status

Work in progress. Do not submit this directory for manufacture until the
package has been validated and marked ready.
