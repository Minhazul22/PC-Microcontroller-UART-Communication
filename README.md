# PC–Microcontroller UART Communication: Four-LED Control

A documentation-focused embedded-systems laboratory project describing a PC terminal interface for controlling four user LEDs on the TI Tiva TM4C1294XL evaluation board over UART.

> **Source-code note:** The original laboratory implementation is not included because permission to redistribute it has not been granted. This repository documents the design and reported behavior; it does not claim to provide a reproducible firmware build.

## Project Overview

The laboratory task explores communication between a PC and a microcontroller using a UART serial interface. The PC terminal sends text commands; the microcontroller interprets the action and LED number to turn one of four user LEDs on, off, or toggle its state. A board switch (SW1) is used to report which LEDs are currently on.

## Goals

- Receive text commands through UART0.
- Determine the requested operation and LED number.
- Turn the selected LED on, turn it off, or toggle it.
- Use SW1 to report the current LED states to the terminal.
- Configure serial communication for a target baud rate of 9600 bit/s.

## Hardware and Tools

| Component | Role |
|---|---|
| TI Tiva TM4C1294XL evaluation board | Microcontroller platform and user LEDs |
| PC terminal | Sends control commands and displays status |
| UART0 | Serial communication interface |
| SW1 | Requests LED-state feedback |
| Code Composer Studio | Development/debug environment described in the lab material |

The presentation describes UART0 with a target rate of 9600 bit/s and an 8-N-1 serial format, using a 16 MHz system-clock assumption for the baud-rate calculation. These are the documented lab settings, not a new independent measurement.

## Command Model

The presentation's flowchart shows three action characters:

| Character | Meaning |
|---|---|
| `+` | Turn the selected LED on |
| `-` | Turn the selected LED off |
| `~` | Toggle the selected LED |

The flowchart branches for LED numbers 1 through 4 and includes an invalid-LED-number path. The exact command grammar, separators, and terminal response strings are not fully specified in this public summary; they are not guessed here.

## System Flow

1. The user enters a command in the PC terminal.
2. The command is received over UART0.
3. The firmware identifies the action and LED number.
4. The selected LED operation is performed, or the invalid-number path is taken.
5. SW1 is used to request a report of the LEDs that are currently on.

See the [system overview](docs/system-overview.md) and the [command model and proposed test matrix](docs/command-protocol.md). An original flow diagram is available in [Mermaid source format](diagrams/uart-command-flow.mmd).

## Reported Results

The accompanying lab presentation states that the tasks were completed with the expected output. This is reported academic project context; no independent retest is claimed by this repository.

## Repository Contents

- [System overview](docs/system-overview.md) — components, conceptual data flow, and documented UART settings.
- [Command protocol](docs/command-protocol.md) — action meanings, known gaps, and a proposed manual test matrix.
- [UART command flow diagram](diagrams/uart-command-flow.mmd) — editable Mermaid diagram authored for this repository.

## Limitations

- Firmware source code is omitted due to redistribution permission constraints.
- The exact command syntax and terminal output are not fully documented here.
- The test matrix is a proposed checklist; tests should only be marked as passed after executing them.
- No new measurements or independent hardware tests are claimed.
- Check university rules before sharing original slides, handouts, or figures. The diagram in this repository is an original summary rather than a copy of the slide image.

## Skills Demonstrated

- UART serial communication concepts
- Embedded command parsing
- GPIO/peripheral control
- Handling multiple command actions and invalid input
- Switch input and peripheral-state reporting
- Hardware/software integration and laboratory verification

## Academic Context

Based on a Micro-Controller Lab 4 exercise on controlling a microcontroller from a PC via UART. This repository is a portfolio-oriented design summary, not a replacement for restricted course materials.
