# Text (1)

For reading and printing text to the console. 

## Input

For getting text.

### Get (1)

**Arguments:** No arguments

**Return: ** The input as ascii values. 

Get Text from console until a new-line.

Example code to get input:

```BrainFuck
+,, add Text.Get to the buffer
.,  Call buffer
```

now if the users enters `abc`

then the **memory** will look like: `97 98 99`

## Output

Display text to the Console.

### Print (1)

**Arguments:** `Text`

**Return: ** None

Print `Text` to the console.

Example code to get print input entered:

```BrainFuck
>     move to cell #1
+,,-, get input, see: Text.Input.Get
<     move back cell #0
+..   add Text.Print to the buffer
>[.>] add all input values to the buffer
.     run buffer printing input
```

Now if the user **enters:** `abc`

The **Output** will be: `abc`

And the **Memory:** `1 97 98 99`
