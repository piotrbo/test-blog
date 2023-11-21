Wake-up Java 21 is comming into Smart.
If you are like me finished education on Java 8 language fatures (functional programming with streams and lambda) this is a good moment to recap what language features has been added in last years

https://docs.oracle.com/en/java/javase/21/language/record-patterns.htm
17
http://www.oracle.com/pls/topic/lookup?ctx=javase17&id=GUID-0C709461-CC33-419A-82BF-61461336E65F
Text Blocks
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
results in the following:
    <html>
        <body>
            <p>Hello World.</p>
        </body>
    </html>
