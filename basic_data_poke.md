# Using BASIC to combine POKE statements with DATA statements

In many variants of **BASIC**, including Commodore's, the **DATA** keyword can be a useful alternative to arrays for feeding batches of data into a program *en masse* to populate one or many variables.
The BASIC command **READ** reads one line of data at a time into the specified BASIC variables.

On 8-bit Commodore microcomputers, especially in the early years, one popular way to enter raw machine code programs was to assign every byte of the program and its associated data to a series of DATA statements in BASIC, and then write a simple **loader** consisting usually of a few lines of BASIC, often with a simple loop structure, to read the DATA, store it at an appropriate addresss space where it will not conflict with the operating system kernel (or "kernal" in Commodore's unconventional spelling) or with the BASIC interpreter, and then execute it using the **SYS** statement specifying the start address.

A relatively easy way to learn the fundamentals of this "loader" technique long before one has learned machine language, binary notation or the like, is to use a combination of **POKE** and **DATA** in a short BASIC program to efficiently set several user interface parameters, such as display colours.

## First example: set blue border, black background and white text
```jsx
10 READ A, V
20 IF A + V = 0 THEN END
30 POKE A, V
40 GOTO 10
50 DATA 53280,6
60 DATA 53281,0
70 DATA 646,1
80 DATA 0,0
```

```jsx
LIST
RUN
```

### Explanation
This code snippet is comprised primarly of address-value pairs, saying "please inject this value into this memory address." 
 - Border (address 53280) is set to blue (6)
 - Background (address 53281) is  set to black (0)
 - Text (address 646) is set to white (1)

When A and V, as read from a **DATA** line, both equal 0 (tested on line 20) the program exits with the **END** command, thereby breaking out of the potentially infinite loop setup by the **GOTO** instruction. The program will READ-then-POKE in a loop until double-zero DATA is encountered.

This can be useful in situations where one wishes to keep changing the amount of data without undue constraint. The values chosen to represent the end of the dataset are arbitrary: while (0, 0) was chosen for this simple example and worked well, this would obviously not be an acceptable choice in a project handling statistical data in which some of the real entries could conceivably equal 0, e.g. *points scored* or *number of endangered birds spotted on the lake today*.
