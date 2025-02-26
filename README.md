# Google-Girls-Hackathon: Combinational Depth Predictor

## Step 1: Collecting Verilog Codes from the internet
Collected the Verilog codes from various websites and also used some of my own verilog codes.

## Step 2: Synthesizing the RTL Circuit using Yosys
- Synthesizing the RTL circuit to get the Fan IN, Fan OUT and Number of Gates which is used in the dataset.
```
yosys
read_verilog test.v
synth
stat
write_verilog output.v
```

- After running the code I got this output shown below.

![yosys1](https://github.com/user-attachments/assets/318c7b76-ae32-41b0-a59c-71ae98b7ed59)

- This is the netlist of the above synthesis

![yosys2](https://github.com/user-attachments/assets/e0b4e49c-090e-4e62-a752-a9b9b98fb04e)


## Step 3: Timing Analysis done by OpenTimer
Timing Report is obtained by OpenTimer
OpenTimer helped me to find Combinational Depth and Critical Time.
```
read_verilog circuit.v
read_celllib cells.lib
read_sdc constraints.sdc
report_path
```

## Step 4: Creating Dataset by collecting Values from Yosys and OpenTimer in CSV File
I am able to create a total of 1000 dataset and used in my Machine Learning Model
![image](https://github.com/user-attachments/assets/812aa0bb-42e8-4eeb-99ef-4f0bdf673b21)


## Step 5: Implementing The ML Model
Implemented XGBoost Regressor Model to find the Combinational Depth using the Dependent Variables (Critical Time, Gate Count, Fan_IN, Fan_OUT)
I coded in Jupyter Notebook using VSCode

- After Training the XGBoost Model
![image](https://github.com/user-attachments/assets/c654137a-2672-41e2-a599-4195eaa81d73)

- Calculated Mean Absolute Error(MAE), Mean Squared Error(MSE) & R2Score

![image](https://github.com/user-attachments/assets/e30ca49f-dd16-48cd-858d-2f8f319c0462)

I am successfully implemented a model in which i got a 0.954 R2Score.

-Graph of Accuracy: Predicted v/s Actual Combinational Depth
![image](https://github.com/user-attachments/assets/f1587652-c14c-4733-b2e3-026af4e3b18f)
