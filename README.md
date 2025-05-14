# Learn ![C#](https://img.shields.io/badge/c%23-%23239120.svg?style=for-the-badge&logo=csharp&logoColor=white)

## Resources

- [ ] [Microsoft](https://learn.microsoft.com/en-us/training/modules/csharp-write-first/)

## BASIC SYNTAX

:warning: C# is : :warning:

- Case sensitive
- `;` is required at the end of the statments, it  tells the compiler when the command ends

___

### **Print things**

`Console.WriteLine()`
Appends a new line after the output.

```cs
Console.WriteLine("Hello World");
```

:warning: **NOTES** :warning:  

- [ ] It is case sensitive.  
- [ ] `Console` is a class.  
- [ ] `WriteLine`is a method.
- [ ] A return will be added to the end of the line.

___

`Console.Write()`

```cs
Console.Write("Congratulations!");
Console.Write(" ");
Console.Write("You wrote your first line of code.");

// --> Congratulations! You wrote your first lines of code.
```

:warning **NOTES** :warninng:

- [ ] This is one continuou line.
- [ ] `Console` is the class.
- [ ] `Write()` is the method.
- [ ] There is no "return" or new line at the end.

___

`Console.Write() and Console.WriteLine()`

```cs
Console.WriteLine("Congratulations!");
Console.Write(" ");
Console.Write("You wrote your first line of code.");

/* --> 
Congratulations!
 You wrote your first lines of code.
*/
```

:warning: **NOTES** :warning:

- [ ] There is a "enter" at the end of Congratulations.
- [ ] The rest of it is all on one line.

___

### Data Types  

1. Literal String

- use double quotes ` "  " `  

   :computer: Example :computer:

    ```cs
    "Hello World"
    // -> Hello World
    ```

___

### **Classes**

#### **`Console`**  

##### Methods

<!-- template of methods 

`Write()`

> Prints out what inside the () without a return at the end.

___
-->

___

`WriteLine()`

> prints out what's inside the () to the console and adds a return at the end.  

___

`Write()`

> Prints out what inside the () without a return at the end.

___

## ERROR HANDLING

### How to read error messages

```cs
(1,1): error CS0103: The name 'console' does not exist in the current context
```

`(1,1)`
> the line and the column where the error is  

`The name 'console' does not exist in the current context`
> The rest of the message is what is wrong with it.

___

### Actual error messages & solutions

___

#### error CS0103

```cs
// code
console.WriteLine("Hello World");

// error message
(1,1): error CS0103: The name 'console' does not exist in the current context
```

> change `console` to `Console` with a capital C
>> `(1,1)` shows that the error happened on line 1 column 1 which would be the letter `c` in `console`

___
#### error CS1012

```cs
// code
Console.WriteLine('Hello World!');

// error message
(1,19): error CS1012: Too many characters in character literal
```

> change the single quotes to double quotes.
>> `(1,19)` shows that the error happened on line 1 at the 19th character which is the `'` right before `Hello`

## EXCERSICES

[Simple Website](github.com/wk642/learn-csharp/simple-website-c-sharp)
