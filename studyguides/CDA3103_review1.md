# CDA 3103 Computer Organization & Architecture - Exam 1 Review

<!-- Use 'img' tags when image resizing is needed. -->

<p style="text-align:center">
    <a href="../textbooks/CDA3103_textbook.pdf">textbook</a> |
    <a href="https://quizlet.com/830254006/cda-3103-exam-1-flash-cards">quizlet</a> |
    <a href="https://www.youtube.com/playlist?list=PLjrUT4yHnh3JxMGJmUCBEZklpVlTJZS94">recitations</a>
</p>

### SI Unit Prefixes
| Prefix    | Symbol    | Value         |
|-----------|-----------|---------------|
| femto-    | f         | $10^{-15}$    |
| pico-     | p         | $10^{-12}$    |
| nano-     | n         | $10^{-9}$     |
| micro-    | $\mu$     | $10^{-6}$     |
| milli-    | m         | $10^{-3}$     |
| kilo-     | k         | $10^3$        |
| mega-     | M         | $10^6$        |
| giga-     | G         | $10^9$        |
| tera-     | T         | $10^{12}$     |
| peta-     | P         | $10^{15}$     |

## 1. Introduction to Computer Organization and Architecture

- The modern *computer*:
    - Electronic
    - Digital (works on binary data)
    - General purpose
    - Automatically follows lists of instructions to solve a problem
- These lists of instructions are *algorithms*
    - Implemented using computers to create *programs*
- Simplest component of a computer is integrated circuit (IC)
    - Evolved from vacuum tube, to transistor, to IC, to very large IC, to ultra-large IC

### Basic Laws and Principles
| Name                                              | Meaning                                                                               |
|---------------------------------------------------|---------------------------------------------------------------------------------------|
| Principle of Equivalence of Software and Hardware | *"Any task done by software can be done by hardware, and vice-versa"*                 |
| Moore's Law                                       | *"The density of transistors (modern, silicon chips) doubles every year (18 months)"* |
| Rock's Law                                        | *"The cost of capital to build semiconductors doubles every 4 years"*                 |

- The continuation of Moore's Law depends on the discontinuation of Rock's Law, and vice-versa
- Computer architecture: the concepts and principles that define a computer
    - <ins>Ex</ins>: circuit design, control signals, memory types
- Computer organization: the physical implementation of architecture specifications
    - <ins>Ex</ins>: instruction sets, data types, I/O mechanisms
- No clear distinction between matters related to either architecture or organization

>**Example:**
>The fact that a multiply instruction is available is a computer architecture issue.
>How that multiply is implemented is a computer organization issue.

- *Computer Level Hierarchy* organizes different levels of computer abstraction
    - Organization & architecture deals with levels 4-0

### Computer Level Hierarchy
| Level | Name                  | Description                                                                   | Example               |
|:-----:|-----------------------|-------------------------------------------------------------------------------|-----------------------|
| 6     | User                  | Program execution, user interface                                             | Executing programs    |
| 5     | High-Level Language   | Programming in a high-level language                                          | Python                |
| 4     | Assembly Language     | Programming assembly language                                                 | RISC-V                |
| 3     | System Software       | Controls executing processes<br>Protects system resources                     | Operating System      |
| 2     | Machine               | Instruction Set Architecture<br>Programs run directly on machine              | Executable binary     |
| 1     | Control               | Control units<br>Decodes, executes instructions<br>Moves data through system  |                       |
| 0     | Digital Logic         | Transistors, logic gates                                                      | Computer parts        |

- Microcode is code written in assembly or machine language that is bound to hardware
- Hardwiring is physical combination of logic gates to create programs
    - Both microcoding and hardwiring produce microprograms
- Control units ensure proper decoding/execution of instructions
- Instruction Set Architecture (ISA) is set of instructions specific to architecture of machine
    - <ins>Ex</ins>: x86, ARM, RISC-V 

### Measures of Data Volume (in Bytes)
| Decimal       |               |               | Binary        |               |               |               |  
|---------------|---------------|---------------|---------------|---------------|---------------|---------------|
| **Prefix**    | **Notation**  | **Amount**    | **Prefix**    | **Notation**  | **Amount**    | **% Larger**  |
| kilo-         | KB            | $10^3$        | kibi-         | KiB           | $2^{10}$        | 2%            |
| mega-         | MB            | $10^6$        | mibi-         | MiB           | $2^{20}$        | 5%            |
| giga-         | GB            | $10^9$        | gibi-         | GiB           | $2^{30}$        | 7%            |
| tera-         | TB            | $10^12$       | tebi-         | TiB           | $2^{40}$        | 10%           |
| peta-         | PB            | $10^15$       | pebi-         | PiB           | $2^{50}$        | 13%           |

- There exist larger measures of data volume and SI unit prefixes, but they will not be on the exam
- A *clock cycle* is the basic unit of time in a CPU
    - Synchronized to a clock signal

### Common Units of Measurement in Computing
| Measure                   | Description                                       | Unit              | Notation  | Typically         |
|---------------------------|---------------------------------------------------|-------------------|-----------|-------------------|
| Clock frequency           | Number of cycles per second                       | Hertz  ($s^{-1}$) | Hz        | GHz               |
| Clock speed               | Time taken to complete one cycle                  | second            | s         | ns                |
| Instructions per cycle    | Average number of instructions executed per cycle |                   |           | 0.5-3             |
| Time                      |                                                   | second            | s         | ms, $\mu$ s       |
| Length                    |                                                   | meter             | m         | mm, $\mu$ m, nm   |

- Processor speed typically measured using clock frequency
- A *byte* is smallest addressable unit of memory
    - Almost always 8 bits
    - To represent volume in bits, use lowercase *b*

TODO BCD, etc

## 2. Von Neumann Architecture

- *Von Neumann Architecture* is basic form of computer architecture, consists of:
    1. Processor
        - <ins>Ex</ins>: CPU
    2. Memory
        - <ins>Ex</ins>: RAM
    3. Data Input & Output (I/O)
        - <ins>Ex</ins>: Data buses, user input devices
- The processor performs the calculations
- Memory holds data and programs for access by processor
    - Different from storage, which provides long-term storage (typically HDD or SSD)
- I/O mechanism handles valuable user input

><p style="text-align:center">   <!-- `style` attribute not supported by GFM -->
>    <img src="../images/CDA3103_Von_neumann.png" alt="Von Neumann Architecture" width=600>
></p>
>
>- The *program counter* specifies the address of the next instruction
>- *Instruction set cycle* performed by **control unit**
>    - **Fetch** the instruction from memory at the program counter
>    - **Decode** the instruction to know what operation to perform on what operands
>    - **Execute** the specified operation and move the program counter
>- Operands, results stored in **registers** of CPU
>    - Small, incredibly fast storage
>- **Arithmetic logic unit** (ALU) performs the actual operations

- *Von Neumann bottleneck* is single path connecting processor and memory
    - Limits data transfer speed
- *Parallel processing* involves the application of multiple processors at once
- Modern computers are not strictly von Neumann-based
    - More performant, capability for parallel processing
    - Circumvents von Neumann bottleneck
- Computers can contain multiple cores or multiple processors
    - Multi-core processors share memory (L2 cache), making them slower than multiple processors
    - Multiple cores do not share L1 cache
- *Linker* links binary executables to library routines
    - Libraries compiled to `.dll` (Windows), `.so` (Linux), and `.dylib` (MacOS) files
- *Loader* loads executables from storage into memory
    - Increases performance, since storage must be read sequentially
- System bus used to synchronize operations between processors and processor components
    - **Data bus:** Moves data between registers, memory, and I/O mechanism
    - **Address bus:** Sends address of data being accessed by data bus from CPU to memory
    - **Control bus:** Moves control signals between CPU, memory, and I/O mechanism
- Control signals specify how data transfer will take place

## 3. Positional Number Systems

| Number System | Base (Radix)  | Digits    | Bits per digit            | Literal Form      | C literal |
|---------------|:-------------:|:---------:|:-------------------------:|:-----------------:|:---------:|
| Binary        | 2             | 0, 1      | 1                         | $N_2$             | 0bN       |
| Octal         | 8             | 0-7       | 3                         | $N_8$             | 0oN       |
| Decimal       | 10            | 0-9       | <small>*varies*</small>   | $N_10$            | N         |
| Hexadecimal   | 16            | 0-9, A-F  | 4                         | $N_16$            | 0xN       |

- Digits A-F in hexadecimal
    - Corresponding to values 10-15
    - Also representable as a-f
- Numbers in these systems represents as a sum of products
    - Each digit multiplied by its positional value

>**Example:** Convert $147.A_{16}$ to decimal.
>
>| Position  | 2                | 1                 | 0                 | -1                    |
>|-----------|------------------|-------------------|-------------------|-----------------------|
>| Digit     | 1                | 4                 | 7                 | A                     |
>| Product   | $1 \bullet 16^2$ | $4 \bullet 16^1$  | $7 \bullet 16^0$  | $10 \bullet 16^{-1}$  |
>
>$16^2 + (4 \bullet 16) + 7 + \frac{10}{16} = 327.625_{10} \checkmark$

## 4. Binary Representation of Numbers

TODO more on 1's complement

- *Binary* is the representation of numbers in base-2
    - Also represent closed and open or on and off, respectively
    - Binary digits, a.k.a. *"bits"*
- *Most-significant bit* (MSB) is leftmost bit
- *Least-significant bit* (LSB) is rightmost bit
- Sign-extension involves filling leftmost bits with previous MSB
- Computers represent binary in three ways:

| Name           | Representation of Negatives  |
|----------------|------------------------------|
| Sign-Magnitude | MSB is `1`                   |
| 1's Complement | Flip all bits                |
| 2's Complement | Flip all bits, add 1         |

- Positive numbers are the same between representations
- Conversions from decimal to binary:
    1. Convert absolute value of number to binary (see below)
    2. If negative, perform the action specific to the representation

>**Example:** Convert $137_{10}$ to binary, padded to 16 bits.
>
>Closest powers of 2 are 128, 64, 32, 16, 8, 4, 2, 1 
>```c
>⌊137 / 128⌋ = 1 // Since 128 = 2^7, bit at position 7 is 1
>137 - 128 = 9 
>⌊9 / 8⌋ = 1     // Divide by next smallest power of 2; Since 8 = 2^3, bit at position 3 is 1
>9 - 8 = 1
>⌊1 / 1⌋ = 1     // Divide by next smallest power of 2; Since 1 = 2^0, bit at position 0 is 1
>```
>
>| Position  | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
>|-----------|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
>| Digit     | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 |
> 
>$137_{10} = 10001001_2 = 0000000010001001_2 \checkmark$

- Overflow is when final carry is 1
    - May cause numbers to "wrap around" to a different sign
- Addition without overflow is the same between representations
    - Going from right-to-left, add each bit according to the table below

| # of 1's  | 0 | 1 | 2 | 3 |
|-----------|:-:|:-:|:-:|:-:|
| Result    | 0 | 1 | 0 | 1 |
| Carry     | 0 | 0 | 1 | 1 |

- Subtraction is the same, except second number is negated according to representation
- For sign-magnitude results, you just have to know the result and resulting sign
- For 1's complement, overflow is added to number at position 0
- For 2's complement, overflow is disregarded

>**Example:** Subtract $23_{10}$ from $-13_{10}$ using 1's complement.
>
>$-13_{10} = -(00001101_2) = 11110010_2$
>
>$-(23_{10}) = -(00010111_2) = 11101000_2$
>```c
>  111 
>   11110010
> - 11101000
>-----------
>   11011010 \\ Adding overflow of 1, we get 11011011
>```
>$11011011_2 = -(00100100_2) = -36_{10} \checkmark$

## 5. Character Encodings

- Memorization of encoding tables is unnecessary for exam
- *Binary-coded decimal* (BCD) encodes characters using 4 bits
    - Encodes digits 0-9 in their decimal form
- Special BCD "zones" represent signedness
    - **Unsigned:** `1111`
    - **Positive:** `1100`
    - **Negative:** `1101`

>**Example:** Numbers larger than 9 are comprised of multiple BCD digits.
>
> $-13 = (1101\ 0001\ 0011)_{BCD}$

- *EBCDIC* extends BCD by encoding characters using 8 bits
    - First widely-used encoding to support letter case

<p style="text-align:center">
    <img src="../images/CDA3103_EDBDIC_table.png" alt="EDBDIC Table" width=80%>
</p>

- *ASCII* is an 7-bit character encoding
    - Most computers store as 8-bits, or a *byte*
    - First 127 Unicode characters
- Last, *parity bit* used to check for errors
    - If odd parity, number of `1`s must be odd, vice-versa
<p style="text-align:center">
    <img src="../images/CDA3103_ASCII_table.png" alt="ASCII Table" width=80%>
</p>

- *Unicode* extends ASCII to 16 bits
    - Encodes scripts used by all world languages

## 6. Boolean Algebra

- In computers, bits `1` and `0` are stand-ins for *true* and *false*, respectively
- *Elementary operations* are product, sum, and complement
    - Combine to create Boolean (logical) expressions
- Existence of both AND and OR forms for each identity is *Duality Principle*

### Common Boolean Operations
| Operation         | Shorthand | Notation          | C Equivalent  | Meaning                   |
|-------------------|-----------|-------------------|---------------|---------------------------|
| Boolean Product   | AND       | x $\bullet$ y, xy | `x && y`      | x *and* y                 |
| Boolean Sum       | OR        | x + y             | `x \|\| y`    | x *or* y                  |
| Complement        | NOT       | x', $\bar{x}$     | `~x`          | *not* x                   |
| Exclusive OR      | XOR       | x $\oplus$ y      | `x ^ y`       | x *or* y, *but not both*  |

### Boolean Identities
| Name                  | AND (CPOS) Form           | OR (CSOP) Form            |
|-----------------------|---------------------------|---------------------------|
| Identity Law          | 1x = x                    | 0 + x = x                 |
| Null (Dominance) Law  | 0x = 0                    | 1 + x = 1                 |
| Idempotent Law        | xx = x                    | x + x = x                 |
| Inverse Law           | xx' = 0                   | x + x' = 1                |
| Commutative Law       | xy = yx                   | x + y = y + x             |
| Associative Law       | (xy)z = x(yz)             | (x + y) + z = xy + xz     |
| Distributive Law      | x + (yz) = (x + y)(x + z) | x(y + z) = xy + xz        |
| Absorption Law        | x(x + y) = x              | x + xy = x                |
| DeMorgan's Law        | (xy)' = x' + y'           | (x + y)' = x'y'           |
| Double Complement Law | x'' = x                   | <small>*same*</small>     |

### Derived Boolean Identities
| Name              | Form                      | Property          |
|-------------------|---------------------------|-------------------|
| Redundancy        | x + x'y = x + y           | Absorption Law    |
| Consensus Theorem | xy + y'z + xz = xy + y'z  | Absorption Law    |
| Definition of XOR | x $\oplus$ y = x'y + xy'  |                   |

- When applying DeMorgan's Law, ensure that order of operations is preserved
- "Mutual exclusion" is another form of the Absorption Law
- The Consensus Theorem can be proven using the other laws
    - "y has no effect on the final truth value given x + z, so xz implies xy + y'z"
- *Boolean functions* accept Boolean variables (conditions) and produce a new condition
    - Rely on the Boolean expressions they are defined as
- *Truth tables* present every possible combination of Boolean variables (x, y, z, ...)
    - Number of possible combinations (rows) equal to $2^n$, where $n$ is number of variables
    - It helps to list the combinations as they are below, as they translate well to K-maps

>**Example:** Create a truth table for $F(x,y,z) = xy' + z(x' + y)$
>
>| x | y | z | F |
>|:-:|:-:|:-:|:-:|
>| 0 | 0 | 0 | 0 |
>| 0 | 0 | 1 | 1 |
>| 0 | 1 | 0 | 0 |
>| 0 | 1 | 1 | 1 |
>| 1 | 0 | 0 | 1 |
>| 1 | 0 | 1 | 1 |
>| 1 | 1 | 0 | 0 |
>| 1 | 1 | 1 | 1 |

## 7. Simplifying Boolean Expressions

- *Sum-of-Product* (SOP) is form $wx + yz$
    - A.k.a. *"1-dominant"*; if any term is `1`, the expression equals `1`
    - Generally easier to work with
- *Product-of-Sum* (POS) if form $(w + x)(y + z)$
    - A.k.a. *"0-dominant"*; if any term is `0`, the expression equals `0`

>**Example:** Convert $xy' + z$ to canonical sum-of-products (CSOP) form.
>
>```c
>xy' + z =
>xy'(z + z') + z(x + x')(y + y') =          // Inverse Law 
>xy'z + xy'z' + xyz + x'yz + xy'z + x'y'z = // Distributive Law
>xy'z + xy'z' + xyz + x'yz + x'y'z          // Idempotent Law
>```

- The form of an expression is *canonical* when it is in simplest form and every term contains all variables
    - Each product, when simplified, is a term
- *Karnaugh maps* (K-maps) can be used to simplify expressions intuitively
    - Products can be formed from groups of bits of size $2^n, n \in Z$
    - It might be helpful to create a truth table first and then convert it to a K-map
    - Not directly tested on the exam, but may be faster than using identities
- By using identities, K-maps, or truth tables, Boolean expressions can be converted to their simplest form
    - Each row in a truth table corresponds to a term
    - Use to easily convert function to CSOP

>**Example:** Use Boolean identities to simplify $F(x,y,z) = (x' + y + z')' + xy'z' + yz + xyz$.
>
>| F(x,y,z) | = (x' + y + z')' + xy'z' + yz + xyz   |                   |
>|----------|---------------------------------------|-------------------|
>|          | = xy'z + xy'z' + yz + xyz             | DeMorgan's Law    |
>|          | = xy'z + xy'z' + yz                   | Absorption Law    |
>|          | = xy'(z + z') + yz                    | Distributive Law  |
>|          | = xy' + yz $\checkmark$               | Inverse Law       |

>**Example:** Use a K-map to simplify $F(x,y,z) = y(x'z + xz) + x'yz' + xy'z$.
>
>| x \ yz   | 0 0   | 0 1                           | 1 0                           | 1 1                           |
>|:--------:|:-----:|:-----------------------------:|:-----------------------------:|:-----------------------------:|
>| **0**    | 0     | 0                             | <font color="pink">1</font>   | <font color="pink">1</font>   |
>| **1**    | 0     | <font color="cyan">1</font>   |  0                            | <font color="cyan">1</font>   |
>
>Combining the groups into sizes of $2^n$, we see that in the pink group, y and x are the same in both cases,
>which allows us to transform it into the minterm x'y.
>
>When we do the same for the cyan group, we get xz.
>
>From this, we can assert that the function is x'y + xz $\checkmark$

- SOP's can be represented by their minterms
    - Represented as elements in $\sum{m}(...)$
    - Every row in truth table where *F* is `1`, as a product; for each variable, if it is `0`, complement it
    - Each term added to each other
- POS's can be represented by their maxterms
    - Represented as elements in $\prod{M}(...)$
    - Every row in truth table where *F* is `0`, as a sum; for each variable, if it is `1`, complement it
    - Each term multiplied to each other
- Elements of formal representations of the above represented as decimal integers
    - Converted from binary to base-10

>**Example:** List the minterms and maxterms of the function represented by the truth table.
>
>| x | y | F |
>|:-:|:-:|:-:|
>| 0 | 0 | 0 |
>| 0 | 1 | 1 |
>| 1 | 0 | 1 |
>| 1 | 1 | 1 |
>
>Minterms are $\sum{m}(1,2,3)$ (from 01, 10, 11), or x'y + xy' + xy
>
>Maxterms are $\prod{M}(0)$ (from 00), or x + y