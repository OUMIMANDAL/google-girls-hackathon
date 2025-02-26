# google-girls-hackathon

## Step 1: Collecting Verilog Codes from the internet
Collected the Verilog codes from various websites and also used some of my own verilog codes.

## Step 2: Synthesizing the RTL Circuit using Yosys
Synthesizing the RTL circuit to get the Fan IN, Fan OUT and Number of Gates which is used in the dataset.
```
yosys
read_verilog test.v
synth
stat
write_verilog output.v
```
