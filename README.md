# BrainLove

**BrainLove** is a new version of [Brainfuck](https://www.wikiwand.com/en/Brainfuck) , **BrainLove** is designed to let **BrainFuck** interact with the "outside world", this is actions like:

* IO
* Networking
* Get time
* Read Keyboard
* And more

## Why

I fell in love with **BrainFuck**, I felt the main thing holding me back was the <u>interface</u>. Mainly standard **Brainfuck** only really has a text interface, text in (`,`) and text out (`.`). But what if you wanted to do more? Call apis for example, you cant. That is what **BrainLove** is here to change. 

## Standard BrainFuck

This is an explanation of the standard BrainFuck, This is what **BrainLove** will build out from. 

> **Brainfuck** is an [esoteric programming language](https://www.wikiwand.com/en/Esoteric_programming_language) created in 1993 by Urban Müller, and is notable for its extreme minimalism.

[_Wikipedia_](https://www.wikiwand.com/en/Brainfuck)

### The Memory / Tape

BrainFuck has Memory, you can think of it has a list of cell/values, or a tape. This differ from interpreters, but this is how **BrainLove** will do it:

A cell will always be in the range **0-255** (Inclusive), this means when a cell would go to **0** it goes to **255**, and when it goes to **256** it goes to **0**

There is also a **pointer** that starts at cell #0 , the pointer **_Cant_** go to **-1** , if it does the interpreter should raise a error. _Current cell_ Will referee to the cell the **Pointer** is currently at.

### The instructions

Here are the **Standard** BrainFuck instructions. 

| Instruction | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| `>`         | Move the **Pointer** to the **Right**.                       |
| `<`         | Move the **Pointer** to the **Left**.                        |
| `+`         | **Add 1** to the current cell.                               |
| `-`         | **Subtract 1** from the current cell.                        |
| `[`         | **If**  there is a **0** at the current cell jump to corresponding  `]` , if not continue to the next instruction. |
| `]`         | **If**  there is a **Non-0 value** at the current cell jump yo corresponding  `[` , if not continue to the next instruction. |
| `,`         | Read **input** as [Ascii](https://www.wikiwand.com/no/ASCII) and save it to the current cell |
| `.`         | **Output **the [Ascii](https://www.wikiwand.com/no/ASCII) value at the current cell. |







