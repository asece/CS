# Csharp 101 
  
    static void Main(string[] args)
    {
    Console.WriteLine("-----------------------------");
    Console.WriteLine(" {0} to {1}", byte.MinValue, byte.MaxValue);
    Console.WriteLine(" {0} to {1}", int.MinValue, int.MaxValue);
    Console.WriteLine("-----------------------------");

    {
        byte x = 1;
        int j = x;
        Console.WriteLine(j);
        // OK
        Console.WriteLine("-----------------------------");

    }

    {
        int i = 1000;
        // byte b = i; //  Cannot implicitly convert type 'int' to 'byte'.An explicit conversion exists (are you missing a cast?) App1 C:\Users\alexs\OneDrive\Documents\Git Repo\CS\App1\App1\Program.cs	25	Active
        byte b = (byte)i;
        Console.WriteLine(b); // 232 , some of the bits were lost.
        Console.WriteLine("-----------------------------");

    }
    {
        string n = "123456";

        // int i = (int)n; Error CS0030  Cannot convert type 'string' to 'int'   App1 C:\Users\alexs\OneDrive\Documents\Git Repo\CS\App1\App1\Program.cs  31  Active

        int i = Convert.ToInt32(n);
        Console.WriteLine(i); // All good

        Console.WriteLine("-----------------------------");
    }
    {
        string n = "1234";
        // byte i = Convert.ToByte(n);
        // Unhandled exception. System.OverflowException: Value was either too large or too small for an unsigned byte.

        try
        {
            byte i = Convert.ToByte(n);
            Console.WriteLine(i);
        }
        catch (Exception)
        {
            Console.WriteLine("Error at conversion");
        }

        // We can do:
        try
        {
            string str = "true";
            bool b = Convert.ToBoolean(str);
            Console.WriteLine(b);
        }
        catch (Exception)
        {
            Console.WriteLine("Exception at convertion");
        }
        
        Console.WriteLine("-----------------------------");

    }

## Arrays

Array: A data structure used to store a collection of variables of the same type  
`int[] numbers = new int[3];`
or use `var` instead of `int[]`

1st []: inform the compiler we want to declare an array  
2nd []: set the size of the array

Arrays have a fixed size and cannot be changed. It is an object.
Arrays are 0 indexed

    numbers[1] = 1;
    numbers[2] = 2;
    numbers[3] = 3;`

or supply the values of the array at the declaration: `int[] newNumbers = new int[3] { 1, 2, 3 };`

All of the elements are set to 0.
An array of bool is initialized with false

## String  
    string firstName = "Alex"
    string lastName = "Doe"
    string name = fistName + " " + lastName;
 This can be messy. String format can be used. String is mapped with the String class in `.Net Framework`.
ex:
    string name = string.Format("{0} {1}", firstName, lastName);
Format is a static method.  
{} - this are placeholders.  
Other examples:  
    var numbers = new int[3] {1,2,3,4};
    string list = string .Join(",",numbers);  
1st argument - separator  
2nd argument - array we want to combine  
  
Strings are immutable - once created they cannot be changed.
    string name = "Josh";
    char fisrtChar = name[0];
    name[0] = 'm'; <-- Operation not allowed!
There are methods to manipulate strings and modify their values, but new strings are returned.
  
Verbatim Strings:
    string path = "c:\\program\\project"; 
    //too messy
    string path = @"c:\program\project";
  
## Enum  
  
    public enum Shipping
    {
        const int Regular = 1;
        const int Reg = 2;
        const int Air = 3;
    }
    var method = Sipping.Regular;

Enums are  by default expressed with integers. They can be set to byte by using `: byte` after the name of the enum.  
If no value is set in the enum, then the 1st value will be 0 and the next will be incremented by 1.  

    public enum ShippingMethod
    {
        RegularAir = 1,
        RegisteredAir = 2,
        Express = 3 
    }

    class Program
    {
        static void Main(string[] args)
        {
            var method = ShippingMethod.Express;
            Console.WriteLine((int)method);
            //Conversions
            var methodId = 3;
            Console.WriteLine((ShippingMethod)methodId);

            Console.WriteLine(method.ToString());
            //Console.WriteLine always calls the ToString() to whatever value it is passed.

            var methodName = "Express";
            //Get the string and get the number from the enum
            var shippingMethod= (ShippingMethod) Enum.Parse(typeof(ShippingMethod), methodName);
            Console.WriteLine(shippingMethod);
        }
## Reference types and Value types
  
All primitive types are structures, they take no more than 8 bytes.  
Arrays and Strings are Classes 
  
Classes and Structures are treated different at runtime in terms of memory management.  
  
Value Types | Reference Types |
--- | :---: |
**Structures** | **Classes** |
-Allocated on stack | -Need to allocate memory from the heap
-Memory allocation done automatically | -Garbage collected by CLR
-Immediately removed when out of scope |
  
    var object1 = object2;
  
