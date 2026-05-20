//JavaProgram to Generate a Sequence of Numbers Using Stream and Transformation Operator

import java.util.stream.Stream;

public class StreamMapDemo {

    public static void main(String[] args) {

        System.out.println("Original Numbers:");

        Stream.of(1, 2, 3, 4, 5)
                .forEach(n -> System.out.print(n + " "));

        System.out.println("\n\nSquared Numbers:");

        Stream.of(1, 2, 3, 4, 5)
                .map(n -> n * n)
                .forEach(n -> System.out.print(n + " "));
    }
}
