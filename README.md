# Execution Path

## Learning Goals

- Explain how a program executes in Java

## Execution Path in Java

As we've seen before, a Java class with a method with the following signature `public static void main(String[] args)` can be run from the command line.

Your Java classes can also have as many additional methods as you would like, and methods can be called from other methods. For example:

```java
public class SampleClass { 
    public static void main(String[] args) {
        System.out.println("In the main() method");
        displayFirstMessage();
        System.out.println("Back in main()");
        displaySecondMessage();
        System.out.println("back in main()");
        displayCustomMessage("this method will display whatever I want");
        System.out.println("Done in main()");
    }

    public static void displayFirstMessage() {
        System.out.println("Displaying the first message");
    }

    public static void displaySecondMessage() {
        System.out.println("Displaying the second message");
    }

    public static void displayCustomMessage(String message) {
        System.out.println("Displaying a custom message: " + message);
    }
}
```

This class defines the following methods:

- `main()` is the default method that makes the class runnable from the command line
- `displayFirstMessage()` is a method that doesn't take any parameters and always displays the same hardcoded message
- `displaySecondMessage()` is also a method that doesn't take any parameters and always displays the same hardcoded message
- `displayCustomMessage()` is a method that takes a single parameter and uses it to customize the message it displays

Running this code will produce the following output:

```java
In the main() method
Displaying the first message
Back in main()
Displaying the second message
back in main()
Displaying a custom message: this method will display whatever I want
Done in main()
```

As you can see from the output, the execution of the code follows this path:

1. Start in the `main()` method and execute the first statement
2. The second statement is a call to the `displayFirstMessage()` method, which means the JVM will now
go into that method and start executing the statements in that method - we have effectively transferred control
of our program from one method to another
3. The first and only statement in the `displayFirstMessage()` is a `System.out.println()` to display a hardcoded
message, so that's what the program does
4. When the `displayFirstMessage()` method is done, control of the program is returned to where that method was called
5. We are now back in the `main()` method on the third line of that method, which outputs the message "Back in main()"

The execution continues to go back and forth between our methods as indicated above, until there are no more statements
to execute.
