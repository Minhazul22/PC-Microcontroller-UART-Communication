# UART LED Command Model

## What the presentation shows

The flowchart indicates that the firmware examines command-line characters and recognizes three action characters:

| Character | Meaning in the flowchart |
|---|---|
| `+` | Turn on the selected LED |
| `-` | Turn off the selected LED |
| `~` | Toggle the selected LED |

The flowchart then determines the LED number and branches for LED numbers 1, 2, 3, or 4. It also contains an invalid-LED-number path.

## What is not specified here

The images and presentation extract available for this portfolio do not establish the complete command grammar. In particular, they do not conclusively document whether the number comes before or after the action character, what separators are accepted, or the exact terminal response strings.

For that reason, this file describes the action model rather than inventing exact commands. Add concrete examples only after checking your own permitted notes or a demo.

## Recommended manual test matrix

Use this table to plan a demonstration if you still have access to the board and terminal. The expected behavior is derived from the action meanings shown in the flowchart; the tests below are a proposed checklist, not claims of newly executed tests.

| Test | Input condition | Expected behavior to check |
|---|---|---|
| 1 | Valid selection of LED 1 with the on action | LED 1 turns on |
| 2 | Valid selection of LED 2 with the off action | LED 2 turns off |
| 3 | Valid selection of LED 3 with the toggle action | LED 3 changes state |
| 4 | Repeat toggle on the same LED | LED returns to its previous state |
| 5 | Select LED 4 | Operation applies to LED 4 |
| 6 | Invalid LED number | Invalid-number path is handled without operating the wrong LED |
| 7 | Press SW1 | Terminal reports which LEDs are on |
| 8 | Send more than one command in sequence | Command processing continues correctly |

Record outcomes only after executing the tests. Do not label the checks as passed unless you personally observed the results.
