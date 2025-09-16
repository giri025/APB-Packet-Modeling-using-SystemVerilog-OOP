# Experiment 3: Create and Use Classes and Objects to Model APB Packet.
# 212223060068
# Giri
---

## Aim  
To design and verify an **APB (Advanced Peripheral Bus) packet model** using **SystemVerilog object-oriented programming concepts** such as classes and objects, and simulate it using **ModelSim 2020.1**.

---

## Apparatus Required  
- Computer with **Windows OS**  
- **ModelSim 2020.1** (or later)  
- SystemVerilog source code editor  

---

## Description about APB Packet Modeling  
The **Advanced Peripheral Bus (APB)** is part of the AMBA protocol family used for connecting low-bandwidth peripherals.  
In this experiment, we use **SystemVerilog OOP concepts** to model an APB packet.  

- **Classes and Objects** in SystemVerilog allow abstraction and modularity.  
- An APB packet generally contains:  
  - **Address**  
  - **Data**  
  - **Control signals** (Read/Write, Select, Enable, Ready)  
- Using OOP, packets can be **created, initialized, randomized, and reused**, simplifying testbench construction.  

---

## Features  
- Written in **SystemVerilog OOP style**  
- Defines an **APB Packet class** with properties (address, data, control signals)  
- Includes **methods** for packet initialization and display  
- Demonstrates **object creation and manipulation**  
- Simulated using **ModelSim 2020.1**  

---

## Procedure  

1. **Open ModelSim 2020.1**  
   - Launch ModelSim from Start Menu.  

2. **Create a New Project**  
   - `File → New → Project`.  
   - Name it `APB_Packet_Project`.  

3. **Add SystemVerilog Files**  
   - Create a file `apb_packet.sv` → Define the APB Packet class.  
   - Create a file `apb_tb.sv` → Instantiate objects and test the class.  

4. **Compile the Files**  
   - Select both `.sv` files.  
   - Right-click → **Compile Selected**.  
   - Ensure no errors exist.  

5. **Start Simulation**  
   - `Simulate → Start Simulation`.  
   - Select the testbench module (`apb_tb`).  

6. **Add Signals and Run**  
   - Add relevant signals to the waveform.  
   - Run the simulation for required time.  

7. **Analyze Output**  
   - Observe the creation and display of APB packets.  
   - Verify correct modeling of properties and methods.  

---

## SystemVerilog Code   

### APB Packet Class (`apb_packet.sv`)  
```systemverilog
class APB_Packet;
  rand bit [31:0] PADDR;
  rand bit [31:0] PWDATA;
  rand bit        PWRITE;
  rand bit        PENABLE;
  bit [31:0]      PRDATA;

  function new();
    PADDR   = 0;
    PWDATA  = 0;
    PWRITE  = 0;
    PENABLE = 0;
    PRDATA  = 0;
  endfunction

  function void display();
    $display("APB Packet -> PADDR=%0h, PWDATA=%0h, PWRITE=%0b, PENABLE=%0b, PRDATA=%0h",
              PADDR, PWDATA, PWRITE, PENABLE, PRDATA);
  endfunction
endclass

```

### APB Packet Class (`apb_tb.sv`) 
```systemverilog
module tb;
  APB_Packet pkt1, pkt2;

  initial begin
    pkt1 = new();
    pkt2 = new();

    pkt1.PADDR   = 32'h1000;
    pkt1.PWDATA  = 32'hABCD1234;
    pkt1.PWRITE  = 1;
    pkt1.PENABLE = 1;
    pkt1.PRDATA  = 32'h0;

    pkt2.PADDR   = 32'h2000;
    pkt2.PWDATA  = 32'h11112222;
    pkt2.PWRITE  = 0;
    pkt2.PENABLE = 1;
    pkt2.PRDATA  = 32'hDEADBEEF;

    pkt1.display();
    pkt2.display();

    $finish;
  end
endmodule

```
---
### Simulation Output

<img width="1920" height="1080" alt="Screenshot 2025-09-16 132206" src="https://github.com/user-attachments/assets/48265c28-cc0f-4c86-ae96-eb9f3d3f093b" />


Output log will show the APB packet details created using class objects.

(Insert console output screenshot here after simulation)

---

### Result

The design and verification of an APB packet model using SystemVerilog classes and objects was successfully carried out in ModelSim 2020.1.
The experiment demonstrated how OOP concepts simplify modeling and reusability in SystemVerilog testbenches.
