## POC: C sharp application is passing args and using the Path.Combine function to perform an Path traversal

1. Create a C# application
  ```
  dotnet --version
  dotnet new console
  ```

2. dotnet run
```Hello World! => came from Program.cs```

3. Added "Comparator.cs"
```Csharp
// for writeline
using System;
// for Path
using System.IO;

// made sure that this file and Program.cs are in the same namespace
namespace console_app {

        // class declaration
    public static class another {

                // prints the first two arguments
        public static String showArgs(string a1, string a2) {
            return string.Format(@"a1 is {0} and a2 is {1}", a1, a2);
        }

                // creates a path with the third argument
        public static String showDir(string a3) {
            return Path.Combine(a3);
        }
    }
}
```

4 Edited the "Program.cs" file

```CSharp
using System;
using System.IO;
// namespaces are  a way to oragnize classes
namespace console_app
{
    class Program
    {
        static void Main(string[] args)
        {

                   // another is the other class
           Console.WriteLine(another.showArgs(args[0], args[1]));
           Console.WriteLine(another.showDir(args[2]));


           bool pathExists = Directory.Exists(another.showDir(args[2]));
           Console.WriteLine("Boolean pathExists is {0}", pathExists);
           Console.WriteLine("Hello World!");
        }
    }
}
```

5. Payload to take advantage of Path.Combine
```dotnet run me  ..\ ..\Go\```

 ```..\ => 2nd argument```
 ```..\Go\ => third argument```

Remediation: args[1] and args[2] need to be validated and sanitized depending on the function of the application
