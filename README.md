# PC–Microcontroller UART Communication: Four-LED Control

A documentation-focused embedded-systems laboratory project describing a PC terminal interface for controlling four user LEDs on the Texas Instruments Tiva TM4C1294XL evaluation board over UART.

> **Source-code note:** The original laboratory implementation is not included in this repository because permission to redistribute it has not been granted. This repository documents the design and reported behavior only; it does not claim to provide a reproducible firmware build.

## Project Overview

The laboratory task explores how a PC can communicate with a microcontroller over a serial UART interface. A terminal sends text commands; the microcontroller interprets the command and controls one of four user LEDs. A board switch (SW1) is used to report which LEDs are currently on.

## Goals

- Receive text commands through UART0.
- Parse a command to identify one of four user LEDs.
- Turn a selected LED on, turn it off, or toggle its state.
- Use SW1 to report the current LED states to the terminal.
- Configure UART communication using a target baud rate of 9600 bit/s.

## Hardware and Tools

| Component | Role |
|---|---|
| TI Tiva TM4C1294XL evaluation board | Microcontroller platform and user LEDs |
| PC terminal | Sends control commands and displays status |
| UART0 | Serial communication interface |
| SW1 | User input for requesting LED-state feedback |
| Code Composer Studio | Development/debug environment described in the lab material |

The lab presentation describes a UART0 configuration targeting 9600 bit/s with an 8-N-1 serial format. The actual firmware source is intentionally not redistributed here.

## Command Model

The presentation flowchart shows a command-processing loop that checks an input character for one of three actions:

| Action character | Intended action |
|---|---|
| `+` | Turn the selected LED on |
| `-` | Turn the selected LED off |
| `~` | Toggle the selected LED |

The command also identifies an LED number from 1 to 4. The flowchart includes an invalid-LED-number path. Exact terminal syntax, delimiters, and response strings should be confirmed from permitted notes or a demo; they are not specified fully in this documentation.

## System Flow

1. The user enters a command in the PC terminal.
2. The command is received over UART0.
3. The microcontroller checks the action and determines the LED number.
4. The firmware selects the corresponding LED operation.
5. Invalid LED numbers follow an error-handling path.
6. SW1 is used to request a report of the LEDs that are currently on.

## Reported Results

The accompanying lab presentation states that the tasks were completed with the expected output. This statement reflects the reported laboratory result; no independent re-test is claimed in this repository.

## Repository Structure

- `README.md` — overview of the project, command model, and reported behavior.
- `docs/` — supporting design notes.
- `diagrams/` — an original flow diagram may be added here if permitted.

## Limitations

- Firmware source code is not included due to redistribution permission constraints.
- The exact UART command syntax and terminal output are not fully specified here.
- No new measurements or independent hardware tests are claimed.
- This repository describes a university laboratory exercise; consult the relevant course rules before sharing original slides, handouts, or figures.

## Skills Demonstrated

- UART serial communication concepts
- Embedded command parsing
- Digital GPIO/peripheral control
- Handling multiple command actions and invalid input
- Switch input and reporting peripheral state
- Hardware/software integration and lab verification

## Academic Context

Based on a Micro-Controller Lab 4 exercise on controlling a microcontroller from a PC via UART. The original C implementation is omitted; this repository is intended as a portfolio-oriented design summary, not a replacement for the restricted course materials.
