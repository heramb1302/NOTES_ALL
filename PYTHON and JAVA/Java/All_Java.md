**JVM Architecture Block Diagram**

The JVM architecture is traditionally divided into three main subsystems: 

1. **Class Loader Subsystem**: Responsible for loading, linking, and initializing class files.
2. **Runtime Data Area (Memory)**: The memory allocated to the JVM for executing programs.
3. **Execution Engine**: The component that executes the bytecode instructions.


# 1.Class Loader Subsystem:

This subsystem brings `.class` files into the JVM memory. It follows three major phases
- **Loading:** Uses three types of loaders—**Bootstrap**, **Extension**, and **Application Class Loaders**—to find and load binary data for classes.
- **Linking:**
    - _Verification:_ Ensures the bytecode is valid and safe.
    - _Preparation:_ Allocates memory for static variables with default values.
    - _Resolution:_ Replaces symbolic references in the code with direct memory references.
- **Initialization:** Executes static blocks and assigns actual values to static variables
# 2 Runtime Data Area (Memory Area)**

JVM divides its memory into several areas, each with a specific purpose: 
- **Method Area:** Stores class-level data, including metadata, static variables, and constant pool information.
- **Heap Area:** Where all objects and their instance variables are stored. This area is managed by the Garbage Collector.
- **Stack Area:** Created for every thread. It contains **Stack Frames**, which store local variables, partial results, and return values for methods.
- **PC Registers:** Keeps track of the current instruction being executed by a thread.
- **Native Method Stack:** Stores information related to native methods (written in C/C++) called by the application
# 3. Execution Engine
This is the core component that processes bytecode:  
- **Interpreter:** Reads and executes bytecode instructions one by one. It is fast to start but can be slow for repeated code.
- **JIT (Just-In-Time) Compiler:** Compiles and convert bytecode to machine level code.(0 or 1)
- **Garbage Collector (GC):** Automatically identifies and deletes objects that are no longer in use to reclaim heap memory. 

# 4. Supporting Components

- **Native Method Interface (JNI):** A framework that allows Java code to interact with native libraries (C, C++).
- **Native Method Libraries:** The actual collection of C/C++ libraries required for execution
  
#  |Data Type|Description|

|`byte`|Stores whole numbers from -128 to 127|
|`short`|Stores whole numbers from -32,768 to 32,767|
|`int`|Stores whole numbers from -2,147,483,648 to 2,147,483,647|
|`long`|Stores whole numbers from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807|
|`float`|Stores fractional numbers. Sufficient for storing 6 to 7 decimal digits|
|`double`|Stores fractional numbers. Sufficient for storing 15 to 16 decimal digits|
|`boolean`|Stores true or false values|
|`char`|Stores a single character/letter or ASCII values|




| Modifier    | Description                                                                                                                                                                                                     | Try it |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| `public`    | The code is accessible for all classes                                                                                                                                                                          |        |
| `private`   | The code is only accessible within the declared class                                                                                                                                                           |        |
| _default_   | The code is only accessible in the same package. This is used when you don't specify a modifier. You will learn more about packages in the [Packages chapter](https://www.w3schools.com/java/java_packages.asp) |        |
| `protected` | The code is accessible in the same package and **subclasses**. You will learn more about subclasses and superclasses in the [Inheritance chapter](https://www.w3schools.com/java/java_inheritance.asp)          |        |