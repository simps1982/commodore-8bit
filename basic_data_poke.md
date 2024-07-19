# Using BASIC to combine POKE statements with DATA statements

In many variants of **BASIC**, including Commodore's, the **DATA** keyword can be a useful alternative to arrays for feeding batches of data into a program en masse to populate one or many variables.
The BASIC command **READ** reads one line of data (one DATA line statement) at a time, into the specified BASIC variables.

On 8-bit Commodore microcomputers, especially in the early years, one popular way to enter raw machine code programs was to assign every byte of the program and its associated data to a series of DATA statements in BASIC, and then write a simple **loader** consisting usually of a few lines of BASIC, often with a simple loop structure, to read the DATA, store it at an appropriate addresss space where it will not conflict with the operating system kernel (or "kernal" in Commodore's unconventional spelling) or with the BASIC interpreter, and then execute it using the **SYS** statement specifying the start address.

A relatively easy way to learn the fundamentals of this "loader" technique long before one has learned machine language, binary notation or the like, is to use a combination of **POKE** and **DATA** in a short BASIC program to efficiently set several user interface parameters, such as display colours.

## First example: set blue border, black background and white text
```jsx
10 READ A, V
20 POKE A, V
DATA 53280,6
DATA 53281,0
DATA 646,1
```
### Explanation
This code snippet is comprised primarly of address-value pairs, saying "please inject this value into this memory address." 
 - Border (address 53280) is set to blue (6)
 - Background (address 53281) is  set to black (0)
 - Text (address 646) is set to white (1)
