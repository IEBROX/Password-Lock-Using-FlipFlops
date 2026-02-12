# Password Lock System using Flip-Flops

## Overview

This project implements a digital password lock system using D Flip-Flops and logic gates.  
The design is created and simulated in Logisim.

The system verifies a predefined sequence of inputs using sequential logic.  
If the correct sequence is entered, the "Unlocked" LED turns ON.

## Circuit Diagram

![Password Lock Circuit](docs/circuit_diagram.png)

## Working Principle

- Each input bit is stored in a D Flip-Flop.
- A clock signal controls state transitions.
- The CLEAR signal resets the system.
- Logic gates combine flip-flop outputs to check the correct password sequence.
- If all required conditions are satisfied, the UNLOCK output becomes HIGH.

## Components Used

- D Flip-Flops  
- OR Gates  
- NOT Gate  
- Clock  
- Clear Button  
- LEDs (State Indicators + Unlock Indicator)  
- Input switches  

## Inputs

- Clock
- Clear
- Password bits (p1, p2, p3, p4)

## Output

- Unlocked LED

## Logic Description

The system stores each input bit in sequential flip-flops.  
Combinational logic checks whether the stored state matches the predefined password pattern.  
If the pattern matches, the unlock signal becomes active.

## Features

- Sequential state storage
- Reset functionality
- Digital security concept implementation
- Simulation-based verification in Logisim

## Future Improvements

- Add wrong attempt counter
- Add alarm output
- Implement with JK flip-flops
- Convert to hardware using 7474 IC

## Software Used

Logisim Evolution

## Author

Het Patel  
Digital Electronics Project
