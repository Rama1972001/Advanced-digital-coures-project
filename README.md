# Advanced-digital-coures-project
## Above is the report , and below are the details :

This project involves the implementation of an 8-bit comparator using VHDL and the software Active-HDL. The comparator will be structurally designed using two types of 8-bit adders: the Carry Ripple Adder and the Carry Look-ahead Adder. In stage 2, the comparator will also be implemented as a magnitude comparator. The comparator will be made synchronous with no glitches by feeding it through flip-flops with the appropriate clock speed, which will be determined by finding the maximum delay in each type of implementation. The project will include functional verification for the two designs, which will be simulated to ensure proper functioning.

## About the code in the Appendix:

### The first 329 lines of the  code
it is a set of VHDL entities for different AND gates with varying numbers of inputs. Each entity represents a different AND gate with a specific number of inputs, and each one has the same basic structure.

The first line "LIBRARY ieee" and the second line "USE ieee.std_logic_1164.ALL" are used to include the standard logic library and to use the standard logic package defined in the library, respectively.

The following lines define the entity for the AND gate. Each entity has a name (e.g. "and2" for the 2-input AND gate), and a list of ports. The ports are the inputs and outputs of the gate. Each input and output is named with a single letter (e.g. "x" and "y" for the 2-input AND gate) and is of type std_logic.

The next section of code is the architecture. Each architecture has the same basic structure, with a single line of code that assigns the output of the AND gate to the output port (z), using the inputs (x, y, w, n, m, l, h and i) and the AND operator.

The last line of each architecture is "AFTER 7ns" which is an optional delay statement. This will introduce a delay of 7ns in the output after the inputs are applied to the AND gate.

This code defines a set of AND gates with 2 to 9 inputs, and each one has the same basic structure and function. Each entity represents a different AND gate with a specific number of inputs. The architecture of each entity defines the behavior of the AND gate, which is to perform the logical AND operation on the input signals and assign the result to the output signal.

### The next 140 lines :
This is a VHDL code for a 1-bit full adder (FA) and an 8-bit carry ripple adder/subtractor. The 1-bit FA is an entity with three inputs (a, b, cin) and two outputs (s, cout). The architecture for the 1-bit FA uses three 2-input AND gates, one 3-input OR gate, and one 3-input XOR gate to implement the full adder logic.

The 8-bit carry ripple adder/subtractor is an entity with two 8-bit input vectors (A, B), one 8-bit output vector (S), and one output signal (OVERFLOW). The architecture for the 8-bit carry ripple adder/subtractor uses eight instances of the 1-bit FA and one XOR gate for each bit of the input vectors to implement the adder/subtractor logic. The carry signals are propagated from one full adder to the next, hence the name "carry ripple adder/subtractor".

It is important to notice that in this code there is an error in the 1-bit FA architecture, the use of work.xor3 instead of work.xor2, this could make it not functional.

### The next 70 lines: 
This is a VHDL code for a comparator that uses an 8-bit carry ripple adder/subtractor. The comparator is an entity with two 8-bit input vectors (a, b), a clock input signal (Clk), and three output signals (A_EQUAL_B, A_Greater_Than_B, A_less_Than_B). The architecture of the comparator uses an 8-bit carry ripple adder/subtractor, two 8-bit register, several logic gates (AND, OR, XOR, NOR, INVERTOR) and some buffers to implement the comparator logic.

The comparator first uses the 8-bit carry ripple adder/subtractor to add the two input vectors and generate the sum (SA) and the overflow signal (COF). Then it uses the invertor to generate the inverted sum (NSA). After that, it uses AND gates to generate out1, out2, out3, and out4 signals. Then it uses a NOR gate to generate the AGB signal. Then it uses buffer gates to generate the final output signals A_EQUAL_B, A_Greater_Than_B, A_less_Than_B.
It is important to notice that it also uses a generic register to store the input values and it is using also a flipflop in the output section.


### The next 120 lines:

This code is for a comparator using a carry look-ahead adder. The comparator is used to compare two 8-bit inputs (P and G) and output a 9-bit result (C) indicating if P is greater than, equal to, or less than G.

The first two lines "LIBRARY ieee" and "USE ieee.std_logic_1164.ALL" are used to include the standard logic library and to use the standard logic package defined in the library, respectively. The third line "USE ieee.std_logic_unsigned.ALL" is used to use the package of the std_logic_unsigned type.

The next section defines the "generator" entity which has three inputs P, G and cin (carry-in) and one output C.

The architecture of the generator is defined next, where the internal signals are declared with the keyword "SIGNAL", in this case, a 36-bit vector called "w".

The architecture uses a combination of basic gates such as AND, OR gates to build the generator. The design uses multiple instances of the AND gates and OR gates. Each instance has a specific number of inputs, the number of inputs is determined by the number of signals that need to be connected to that specific instance.

Each AND and OR gate is mapped to the corresponding input signals by using the PORT MAP statement. This statement connects the input and output ports of the gates to the corresponding signals.

The architecture also uses a hierarchical design, the AND and OR gates are connected in a specific way to form the comparator using a carry look-ahead adder. The final outputs of the OR gates are connected to the output C, representing the final result of the comparator.

Overall, this code defines a VHDL entity for a comparator using a carry look-ahead adder. The architecture of the entity uses a combination of basic gates such as AND and OR gates to build the comparator, and it uses a hierarchical design approach. The final outputs of the OR gates are connected to the output C, representing the final result of the comparator.



### The next 88 lines (second stage) :

This code defines two VHDL entities: "comparator_1bit" and "Magnitude_comp".

The first entity "comparator_1bit" is a 1-bit comparator that compares two inputs A and B and outputs 3 signals G, S, and E. The entity has three ports: two input ports A and B, and three output ports G, S, and E.

The architecture of the comparator_1bit uses internal signals NOTA, NOTB, out3, and out4 to perform the comparison. The architecture also uses instances of basic gates such as inverter, AND, OR gates and buffer gates to implement the comparator. The design uses multiple instances of the invertor gates to get the inverted values of A and B, which are then used in the AND gates to get the output G and S. The output E is obtained by using a NOR gate with the inputs out3 and out4.

The second entity "Magnitude_comp" is a 8-bit magnitude comparator that compares two inputs a and b and outputs 3 signals FFOUT1equal, FFOUT2Agreater, FFOUT3Aless. The entity has four ports: two input ports a and b, one input port clock and three output ports FFOUT1equal, FFOUT2Agreater, FFOUT3Aless.

The architecture of Magnitude_comp uses internal signals to perform the comparison and also uses instances of basic gates such as AND, OR, NOR gates, buffer gates and a generic register to implement the comparator. The design uses multiple instances of the AND gates to get the output of the comparison between each bit of a and b, which

are then used in a series of OR gates to get the final output of whether a is greater than, less than or equal to b. The design also uses a generic register to store the input values of a and b and a clock signal is used to control the operations of the comparator. Additionally, the design uses multiple instances of the buffer gates to store the outputs of the comparison in the FFOUT1equal, FFOUT2Agreater, FFOUT3Aless signals.

Overall, this code is implementing a 8-bit comparator using VHDL language and using basic gates such as AND, OR, NOR gates and buffer gates, as well as a generic register to store the input values of a and b and a clock signal to control the operations of the comparator. The design also uses the delay of 7ns in all the gates to make the comparator synchronous with no glitches.




### The next 50 lines ---verification code for stage  1 ---


This code is for a test generator for a comparator circuit. The generator has four output ports, A and B, which are two 8-bit vectors used as inputs for the comparator circuit. The other two output ports are correctgreater, correctless and correctequal, which are signals that indicate whether the comparator circuit's output is correct or not.

The generator has an architecture called "generator" which contains two processes. The first process compares the two input vectors, IN1 and IN2, using an IF-ELSE statement. If IN1 is less than IN2, the correctless signal is set to 1, correctgreater is set to 0 and correctequal is set to 0. If IN1 is greater than IN2, the correctgreater signal is set to 1, correctless is set to 0 and correctequal is set to 0. If IN1 is equal to IN2, the correctequal signal is set to 1, correctgreater is set to 0 and correctless is set to 0.

The second process generates all possible combinations of IN1 and IN2 using nested FOR loops. The values of IN1 and IN2 are updated on every rising edge of the clock signal. Once all possible combinations are generated, the process waits indefinitely. The output vectors A and B are set to the values of IN1 and IN2 respectively. This test generator can be used to verify the functionality of the comparator circuit by comparing the circuit's output with the correct output signals generated by the test generator.

### The next 20 lines ---- Result Analyser ---

The  code is an example of a VHDL module for a result analyzer that checks if the output from a system (myResult1, myResult2, and myResult3) matches the expected correct output (correctgreater, correctless, and correctequal). The module uses an assert statement in a process that waits for a rising edge of the clock signal. If the assert statement evaluates to false, it will trigger a report statement that generates an error message "Incorrect Design". This is useful for checking the correctness of the system and identifying any bugs or errors in the design.


### Then , next 17 lines of code  :


This is VHDL code for a built-in self-test (BIST) for a ripple system. The BIST has an architecture called "ripple" that uses signals for a clock (CLK), two inputs (A and B), and three outputs for correct comparison results (correctgreater, correctless, correctequal). The BIST also instantiates three entities: "TestGenerator", "comparator_from_RA", and "ResultAnalyser". These entities are connected to the architecture using port mapping. The clock signal is set to a frequency of 120 ns with a delay of 60 ns. The TestGenerator entity is used to generate test inputs A and B, the comparator_from_RA entity is used to compare the two inputs and produce comparison results, and the ResultAnalyser entity is used to analyse and check the correctness of the comparison results.



### Then The remained lines of code : ( verification for the 2nd design )



This is VHDL code for a TestGenerator1 entity, which is used to generate test inputs and correct comparison results for a system. The TestGenerator1 entity has ports for a clock (CLK), two inputs (A and B), and three outputs for correct comparison results (correctgreater, correctless, correctequal). The TestGenerator1 entity also has an architecture called "generator" that uses signals for the inputs (IN1 and IN2) and a process to implement the system using behavioral logic. The process compares the two inputs (IN1 and IN2) bit by bit, and based on the comparison, sets the correct comparison results (correctgreater, correctless, correctequal). The input values are assigned to A and B. The TestGenerator1 entity would be used to generate test inputs and correct comparison results for a system, which can then be used to verify the system's functionality.

