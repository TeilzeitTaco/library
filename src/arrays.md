# Common Array Functions

## Debug Printing An Array

In Java:

````java
public final class ArrayPrinting {
    @FunctionalInterface
    public interface ValueMapper<T> {
        Object getValueFor(T element);
    }

    public static <T> void printArray(final T[] array, final ValueMapper<T> valueMapper) {
        final var fString = "%" + String.valueOf(array.length).length() + "d: %s\n";
        for (int i = 0; i < array.length; i++) {
            final var valueString = (array[i] == null) ? "null" :
                valueMapper.getValueFor(array[i]).toString();
            System.out.printf(fString, i, valueString);
        }

        System.out.println();
    }

    public static <T> void printArray(final String message, final T[] array,
                                       final ValueMapper<T> valueMapper) {
        System.out.println(message);
        printArray(array, valueMapper);
    }

    public static <T> void printArray(final T[] array) {
        printArray(array, e -> e.toString());
    }

    public static <T> void printArray(final String message, final T[] array) {
        System.out.println(message);
        printArray(array, e -> e.toString());
    }
}
````

In Python:

````python
````

In FreeBASIC:

````basic
````
