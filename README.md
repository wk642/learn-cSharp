# Learn ![C#](https://img.shields.io/badge/c%23-%23239120.svg?style=for-the-badge&logo=csharp&logoColor=white)

## Resources

- [ ] [Microsoft](https://learn.microsoft.com/en-us/training/modules/csharp-write-first/)

## .NET SDK

`dotnet --list-sdks` will show the versions, as of 2025 May 14th, we want to make sure that at least one of the sdks are version 8.

## EXTENSIONS INSTALLED

- [ ] [C# Dev Kit](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit)

## EXCERSICES

[Simple Website](/simple-website-c-sharp)

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

## RAZOR PAGES

- [ ] Simplifies ASP.NET Core page organization.
- [ ] Keeps related pages and their logic in their own namespace and directory.

### When to use?

- [ ] Generating dynamic UI.
- [ ] Reduce duplication with partial views.
- [ ] Prefer a page-focused approach.

### How to create a Razor Page

#### Uses [this](https://learn.microsoft.com/en-us/training/modules/create-razor-pages-aspnet-core/4-exercise-add-new-razor-page) as reference
1. Open up terminal and goto the directory where you want to create this.
2. Type `dotnet new page --name PizzaList --namespace ContosoPizza.Pages --output Pages`
    > What this does is the following:
    >> The preceding command: Creates these two files in the ContosoPizza.Pages namespace:
    >>> - PizzaList.cshtml -
        the Razor page
    >>> - PizzaList.cshtml.cs -
        the accompanying PageModel class Stores both files in the project's Pages subdirectory.

> To set the `<title>` element for the page, use the @page directive:
>> `ViewData["Title"] = "Pizza List 🍕";`

In this code, the PizzaService will get a list of pizzas, but it was not available to be used yet, so we will need to add it to the dependency injection container.

> `builder.Services.AddScoped<PizzaService>();`
>> This registers the `PizzaService` class with the dependency injection container.
>> `AddScoped` is a method. A new PizzaService object will be created for each HTTP request.

At the top of the file
> `using`
>> tells the file that we will be using the types.

``` cs
public class PizzaListModel : PageModel
{
    // creating a private variable that will be refrenced to a PizzaService object. 
    // readonly means that this can't be changed after it's set in the constructor.
    private readonly PizzaService _service;

    // This is a property that will be used to store the list of pizzas.
    // IList<Pizza> type where the PizzaList property will hold a list of Pizza objects.
    // It is set to default! to let the compiler know that it will be initialized later, so there's no need to check for null.
    public IList<Pizza> PizzaList { get;set; } = default!;

    // A constructor that takes a PizzaService object as a parameter.
    public PizzaListModel(PizzaService service)
    {
        _service = service;
    }

    // Adding page handler for HTTP POST.
    public IActionResult OnPost()
    {
       if (!ModelState.IsValid || NewPizza == null)
       {
           return Page();
       }

       _service.AddPizza(NewPizza);
        // The RedirectToAction method is used to redirect the user to the Get page handler, which will re-render the page with the updated list of pizzas.
       return RedirectToAction("Get");
    }

    // An OnGet method is defined to aget the list of pizzas from the PizzaService object and store it in the PizzaList property.
    public void OnGet()
    {
        PizzaList = _service.GetPizzas();
    }
}

```

> `[BindProperty]`
> `public Pizza NewPizza { get; set; } = default!;`
>
>> - NewPizza is a Pizza object.
>> - The BindProperty attribute is used to bind the NewPizza property to the Razor page. When an HTTP POST request is made, the NewPizza property will be populated with the user's input.
>> The default! keyword is used to initialize the NewPizza property to null. This prevents the compiler from generating a warning about the NewPizza property being uninitialized.
