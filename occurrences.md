// JavaProgram to Count the Number of Occurrences of an Element in a List Using Generic Class

import java.util.ArrayList;
import java.util.List;

class CountOccurrences<T> {

    int countElement(List<T> list, T element) {

        int count = 0;

        for (T item : list) {

            if (item.equals(element)) {
                count++;
            }
        }

        return count;
    }
}

public class GenericCount {

    public static void main(String[] args) {

        List<Integer> numbers = new ArrayList<>();

        numbers.add(10);
        numbers.add(20);
        numbers.add(10);
        numbers.add(30);
        numbers.add(10);

        CountOccurrences<Integer> obj = new CountOccurrences<>();

        System.out.println("Occurrences = " +
                obj.countElement(numbers, 10));
    }
}
