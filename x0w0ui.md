Model: Legacy

---

> in java 8 i see possible heap pollution with varargs how can i take care of that

---

Heap pollution is a situation in Java where an incorrect type of object is stored in an array that was declared with a different type. This can occur with varargs method calls, because arrays in Java are covariant, meaning that an array of a subclass type can be used where an array of a superclass type is expected.

To avoid heap pollution in varargs methods, you can follow these guidelines:

1.  Use the Java Generics framework to specify the type of objects that can be stored in the array. For example, if you have a method that takes an array of strings, you can declare it as follows:

typescript

```typescript
public static void myMethod(String... args) { ... }
```

2.  Check the type of the objects being passed to the varargs method and ensure that they are of the correct type. For example:

typescript

```typescript
public static void myMethod(String... args) {
    for (String arg : args) {
        if (!(arg instanceof String)) {
            throw new ClassCastException("Incorrect type of object passed to method");
        }
    }
}
```

3.  Use an array of the correct type instead of a varargs parameter, if possible. For example:

typescript

```typescript
public static void myMethod(String[] args) { ... }
```

By following these guidelines, you can ensure that your varargs methods are safe from heap pollution.

---