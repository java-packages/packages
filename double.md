//Java Program to Double Each Element in a List Using map() and Lambda Expression

import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamMapExample {

    public static void main(String[] args) {

        List<Integer> numbers =
                Arrays.asList(1, 2, 3, 4, 5);

        System.out.println("Original List:");
        System.out.println(numbers);

        List<Integer> doubled = numbers.stream()
                .map(n -> n * 2)
                .collect(Collectors.toList());

        System.out.println("Doubled List:");
        System.out.println(doubled);
    }
}
