Binary Number System
 - Conversion from Decimal to Binary
 - Binary to Decimal
 - Decimal to Hexadecimal

Bits and Bytes
![[Pasted image 20250114183745.png]]
 - 4 Bits Represent a nibble 
 - A,B,C,D,E,F = {10,11,12,13,14,15} in Hexadecimal
 - 8 Bits Represent a Byte
 ![[Pasted image 20250114184103.png]]
 We can Use Windows Calculator in Programmer Mode to convert between Hexadecimal, Decimal, Binary and Octal. 

---

### Encoding

![[Pasted image 20250114184517.png]]
Ascii Table: American Standard Code for Information Interchange

![[Pasted image 20250114185037.png]]
RGB: Red Green Blue Color Encoding in Hexadecimal or binary

![[Pasted image 20250114185209.png]]
Pixels of Pictures: Show up on screen as colors (Hexadecimal Values) with x and y values. 
Pixels of Video: Same as Pictures but with Time.

---

### **How a CPU Works (Basics)**

#### **1. Core Components of a CPU**

A CPU has several key components:

- **Control Unit (CU):**
    - Directs the flow of data between the CPU, memory, and peripherals.
    - Decodes instructions from programs and orchestrates the execution.
- **Arithmetic Logic Unit (ALU):**
    - Performs mathematical (arithmetic) and logical operations (e.g., addition, subtraction, comparisons).
- **Registers:**
    - Small, fast storage locations inside the CPU that hold data being used immediately.
- **Cache:**
    - Small, high-speed memory within the CPU that stores frequently used instructions and data to speed up processing.
- **Clock:**
    - Synchronizes all CPU operations by generating regular pulses (measured in Hertz, like 3 GHz).

#### **2. Basic Process of How a CPU Executes Instructions**

The CPU operates in cycles known as the **Fetch-Decode-Execute cycle**:

1. **Fetch:**
    
    - The CPU retrieves an instruction from memory (RAM) based on the **Program Counter (PC)**, which keeps track of the next instruction address.
2. **Decode:**
    
    - The Control Unit decodes the instruction to understand what needs to be done. For example:
        - Is it a mathematical operation?
        - Should it move data?
        - Should it compare values?
3. **Execute:**
    
    - The CPU performs the instruction using the ALU, registers, and other components. The result may be stored in memory or used in the next operation.
4. **Repeat:**
    
    - After completing one instruction, the CPU moves to the next instruction in the queue.

#### **3. A Simple Analogy**

Imagine the CPU is like a **chef in a kitchen**:

- **Recipe (Program):**
    
    - A program is like a recipe that the chef follows step by step.
- **Ingredients (Data in Memory):**
    
    - Data in RAM represents the ingredients the chef works with.
- **Utensils (Registers & ALU):**
    
    - Registers are like bowls, measuring cups, and tools the chef uses to prepare ingredients temporarily.
- **Clock (Timer):**
    
    - A timer beeps regularly, ensuring the chef works at a steady pace (e.g., one step every second).

Example:

1. The chef reads a step in the recipe (Fetch).
2. Deciphers what the step says, e.g., "chop onions" (Decode).
3. Executes the step using a knife (Execute).
4. Moves to the next step and repeats the process.

#### **4. A Step-by-Step Example of CPU Execution**

Let’s walk through how a CPU might handle a simple addition operation like `3 + 2`:

1. **Fetch:**
    
    - The CPU fetches the instruction from memory. Example instruction: `ADD R1, R2, R3`.
        - `ADD`: The operation.
        - `R1`: Register where the result will be stored.
        - `R2, R3`: Registers containing the numbers to add (`3` and `2`).
2. **Decode:**
    
    - The CPU's Control Unit decodes the `ADD` instruction to understand it needs to add the contents of `R2` and `R3`.
3. **Execute:**
    
    - The ALU performs the addition:
        - Reads values `3` and `2` from `R2` and `R3`.
        - Adds them together to get `5`.
        - Stores the result `5` in `R1`.
4. **Store/Repeat:**
    
    - The result `5` is stored, and the CPU moves to the next instruction in the queue.