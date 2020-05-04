# CS
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

Arrays

Array: A data structure used to store a collection of variables of the same type
    int[] numbers = new int[3];
or use `var` instead of `int[]`

1st []: inform the compiler we want to declare an array
2nd []: set the size of the array
Arrays have a fixed size and cannot be changed. It is an object.
Arrays are 0 indexed

    numbers[1] = 1;
    numbers[2] = 2;
    numbers[3] = 3;`

or supply the values of the array at the declaration:
    int[] newNumbers = new int[3] { 1, 2, 3 };

All of the elements are set to 0.
An array of bool is initialized with false

