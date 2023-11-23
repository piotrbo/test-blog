Wake-up Java 21 is comming into Smart.
If you are like me finished education on Java 8 language fatures (functional programming with streams and lambda) this is a good moment to recap what language features has been added in last years

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
