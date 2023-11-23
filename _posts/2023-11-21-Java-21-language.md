Wake-up Java 21 has come.
If you are like me, finished education on Java 8 language features (functional programming with [streams](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html) and lambda), this is a good moment to recap what language features has been added in since 2014.

### Sealed Classes

```
public sealed class Shape
    permits Circle, Square, Rectangle {
}
```
```
public final class Circle extends Shape {
    public float radius;
}
```
See [Java 17 doc for sealed-classes-and-interfaces](https://docs.oracle.com/en/java/javase/17/language/sealed-classes-and-interfaces.html)

### Record Patterns
```
record Point(double x, double y) {}

    static void printAngleFromXAxis(Object obj) {
        if (obj instanceof Point(double x, double y)) {
            System.out.println(Math.toDegrees(Math.atan2(y, x)));
        }
    }     
```
See [Java 21 doc for record-patterns](https://docs.oracle.com/en/java/javase/21/language/record-patterns.html)

### Pattern Matching for switch
```
interface Shape { }
record Rectangle(double length, double width) implements Shape { }

record Circle(double radius) implements Shape { }

    public static double getPerimeter(Shape s) throws IllegalArgumentException {
        switch (s) {
            case Rectangle r: return 2 * r.length() + 2 * r.width();
            case Circle c:    return 2 * c.radius() * Math.PI;
            default:          throw new IllegalArgumentException("Unrecognized shape");
        }
    }
```
See [Java 21 doc for  Pattern Matching for switch Expressions and Statements](https://docs.oracle.com/en/java/javase/21/language/pattern-matching-switch-expressions-and-statements.html)


### Text Blocks
```
void writeHTML() {
    String html = """
········    <html>
········        <body>
········            <p>Hello World.</p>
········        </body>
········    </html>
········""";
    writeOutput(html);
}
```

results in the following:
```
    <html>
        <body>
            <p>Hello World.</p>
        </body>
    </html>
```
See: [Java 21 doc for Text Blocks](https://docs.oracle.com/en/java/javase/21/text-blocks/index.html)

### String Templates
```
String name = "Duke";
String info = STR."My name is \{name}";
System.out.println(info);
```
output:
```
My name is Duke
```
See: [Java 21 doc for String Templates](https://docs.oracle.com/en/java/javase/21/language/string-templates.html)

---
Beside language changes that actually makse java mor similar to Scala or Python
There vare added JMV features like:

### Virtual Threads
(important for performannce testers)

Virtual thread isn't tied to a specific OS thread. A virtual thread still runs code on an OS thread. However, when code running in a virtual thread calls a blocking I/O operation, the Java runtime suspends the virtual thread until it can be resumed. The OS thread associated with the suspended virtual thread is now free to perform operations for other virtual threads.
```
Thread thread = Thread.ofVirtual().start(() -> System.out.println("Hello"));
thread.join();
```
Executors let you to separate thread management and creation from the rest of your application.
```
try (ExecutorService myExecutor = Executors.newVirtualThreadPerTaskExecutor()) {
    Future<?> future = myExecutor.submit(() -> System.out.println("Running thread"));
    future.get();
    System.out.println("Task completed");
    // ...
```
See: [Java 21 docs for Virtual Threads](https://docs.oracle.com/en/java/javase/21/core/virtual-threads.html)