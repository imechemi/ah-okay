Exception

When add a throws clause in the method signature, it means that your method is saying I know this is a checked exception 
might get thrown from my method. Some of the example to understand quicker:


### When throws `RuntimeException` (Unchecked)

```java
class Scratch {
    public static void main(String[] args) {
        testThrow();
    }

    public static void testThrow() throws RuntimeException{
        throw new RuntimeException();
    }
}
```

### When throws `Exception` (Checked)
```
class Scratch {
    public static void main(String[] args) { // Editor will warn for not catching
        testThrow(); // Compiler will throw: exception java.lang.Exception; must be caught or declared to be thrown
    }

    public static void testThrow() throws Exception{
        throw new Exception();
    }
}```

### When throws `Exception` (Checked), but method called in try block and also the same exception is caught

```java
class Scratch {
    public static void main(String[] args) {
        try {
            testThrow();  // Compiler does not throw error since you caught the exception
        } catch (Exception e) {
            System.out.println("Caught that exact exception");
        }
    }

    public static void testThrow() throws Exception{
        throw new Exception();
    }
}
```
