# CLI-Hackerrank

CLI-Hackerrank is a MacOS project designed for testing DS&A problems that
require input from the terminal or from Standard Input (stdin). [Hacker Rank](https://www.hackerrank.com/)
has such a requirement but this project need not be limited to working on Hacker Rank 
problems. It also has the benefits of being a quick, lightweight and debuggable  
environment (i.e. with breakpoints) to work through a problem.

# How it works

This command line app is driven by an event loop. Each iteration of the loop
prompts the user to choose a function (one function per problem) to run
and then prompts the user for inputs. The called function could optionally
further describe the inputs.

```swift
while true {
    print("Enter a function, choices are: ", terminator: "")
    for k in funk.keys {
        print(k, terminator: " ")
    }
    print()
    
    if let functionName = readLine(),
        let function = funk[functionName] { // pulling the function from the dictionary
        print("Enter inputs")
        function() // calling the function
    }
    else {
        print("That's not a valid function")
    }
}
```

In an effort to make the program easily extensible, all functions are registered to 
a dictionary named ```funk```. The key is a name or nickname of the function and 
the value is the function itself.

```swift
var funk: [String:()->Void] = [:]
```

After defining a function that will run a test case, add it with a name to the 
dictionary.

```swift
func solveMeFirst() {
    // read integers line by line
    let a = Int(readLine()!)!
    let b = Int(readLine()!)!
    
    // Hint: Type print(a + b) below
    print(a+b)
}
funk["solve"] = solveMeFirst // add this function to the dictionary
                             // note that "solve" can be any string whereas solveMeFirst *is* the function
```
