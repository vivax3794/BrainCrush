# BrainCrush

**BrainCrush** is a new version of [Brainfuck](https://www.wikiwand.com/en/Brainfuck) , **BrainCrush** is designed to let **BrainFuck** interact with the "outside world", this is actions like:

* IO
* Networking
* Get time
* Read Keyboard
* And more

## Why

I fell in love with **BrainFuck**, I felt the main thing holding me back was the <u>interface</u>. Mainly standard **Brainfuck** only really has a text interface, text in (`,`) and text out (`.`). But what if you wanted to do more? Call apis for example, you cant. That is what **BrainCrush** is here to change. 

## Standard BrainFuck

This is an explanation of the standard BrainFuck, This is what **BrainCrush** will build out from. 

> **Brainfuck** is an [esoteric programming language](https://www.wikiwand.com/en/Esoteric_programming_language) created in 1993 by Urban Müller, and is notable for its extreme minimalism.

[_Wikipedia_](https://www.wikiwand.com/en/Brainfuck)

### The Memory / Tape

BrainFuck has Memory, you can think of it has a list of cell/values, or a tape. This differ from interpreters, but this is how **BrainCrush** will do it:

A cell will always be in the range **0-255** (Inclusive), this means when a cell would go to **-1** it goes to **255**, and when it goes to **256** it goes to **0**

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
| `]`         | **If**  there is a **Non-0 value** at the current cell jump to corresponding  `[` , if not continue to the next instruction. |
| `,`         | Read **input** as [Ascii](https://www.wikiwand.com/no/ASCII) and save it to the current cell |
| `.`         | **Output** the [Ascii](https://www.wikiwand.com/no/ASCII) value at the current cell. |

# How BrainCrush changes things 

BrainCrush will modify the `,` and `.` to allow BrainFuck to interface with more things. 

## How will this work? (`,` , `.`)

`,` and `.` would now both **output** to a buffer (They have their own buffers), this buffer would be parsed when it is done.  The _Syntax_ of these buffers are: `<Category> <Function> [arg1] [arg2] ... `

Adding a value to a buffer is as simple as calling `,` or `.` and the value at the current cell would be added to the buffer.  Buffers are _called_ when a value of **0** is added to it. So a example of opening a file would be:

 `<Code for IO> <Code for open function> <file path> 0` And the data of the file would be written to the Memory, more on each function latter.

# How the Docs works

Each Category has it's own markdown file.

Category title _syntax_ `Category Name (Category Code)` The `Category Code` is what you need to add to the buffer.

Function title _syntax_ `function Name (Function Code)` The `Function Code` is what you need to add to the buffer.

When the docs talk about _return_ it means that those value will be written at the current cell, and the cell to it's right

# Current interpreters for BrainCrush

First interpreter for BrainCrush create by me, [BCrushPy](https://github.com/vivax3794/BCrushPy) Still a work in progress.


# Example Programs

## Cat

Print back the users input

```BrainFuck
>     move to cell #1
+,,-, get input, see: Text.Input.Get
<     move back cell #0
+..   add Text.Print to the buffer
>[.>] add all input values to the buffer
.     run buffer printing input
```

## Api Call / Random Number

Gets a random number from [random.org](https://www.random.org/integers/?num=10&min=1&max=6&col=1&base=10&format=plain)

```BrainFuck
    +++++ +++++ +[->++++<]>,[-]< load networking
    +,                           load get
    +++++ ++++[-
        > +++++ +++++ + set 110
        > +++++ +++++   set 100
        > +++++         set 50
        > +++++ +       set 60
        > ++++          set 40
    <<<<<]
    
    >>++++, <+++++ +,, ----, +++,                       load https
    >>>--, <---,,                                       load ://
    <<++++,,, >>-,                                      load www<dot>
    <<-----, >----- --, <----, >+++, <+,-> <-,          load random
    >>, <<++, +++, >+++,                                load <dot>org
    >+, <++, <----, +++++ +, >----, ++, --, <--, +,     load /integers
    >>, >+++++, <<<-----, +++++ ++, >+++++ +++,         load ?num
    >>--, <++, -                                        load =10
    >>--, <<<, ----, <----- --, >>>, <+,                load &min=1
    >>, <<<<-, >----- ---, <+++++ +++++ +, >>>, <+++++, load &max=1
    >>, <<<++, <----- ----, ---, >>>, <-----,           load &col=1
    >>, <<<-, -, <+++++ ++, >++++, >>, <, -,            load &base=10
    >>, <<<+, <----, +++, -----, >-----, <+++++ ++, >>>,load &format=
    <<<----, ----, >, <---, +++++,                      load plain
    [>]<[[-]<]                                          clear memory
    >,                                                  call random api
    <+..->[.>].                                         print response
```

