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

````purebasic
Namespace ArrayPrinter
    'fake generics using preprocessor
    #Macro implementation(createDefault, T)
    #Define ValueMapperType T##ValueMapper
    Type ValueMapperType As Function(ByRef As T) As String

    #If createDefault
    Function default##T##valueMapper (ByRef value As T) As String
        Return Str(value)
    End Function
    #EndIf

    #If createDefault
    Sub printArray OverLoad (array() As T, message As String = "", _    
                            valueMapper As ValueMapperType = @default##T##valueMapper)    
    #Else
    Sub printArray OverLoad (array() As T, message As String = "", _
                             valueMapper As ValueMapperType)
    #EndIf

        If Not message = "" Then
            ? message
        EndIf

        For i As UInteger = LBound(array) To UBound(array)
            ? i, valueMapper(array(i))
        Next
    End Sub

    #Undef ValueMapperType
    #EndMacro

    'add definitions here
    implementation(TRUE, String)
    implementation(TRUE, Integer)
    implementation(TRUE, UByte)

    'use FALSE for UDTs
    'implementation(FALSE, UDT)

    #Undef implementation

    'print an array and its variable name
    #Macro printNamedArray(array)
    ArrayPrinter.printArray(array(), #array + ": ")
    #EndMacro

    #Macro printNamedArrayWithMapper(array, valueMapper)
    ArrayPrinter.printArray(array(), #array + ": ", valueMapper)
    #EndMacro
End Namespace
````
