//Java Program to Concatenate Strings in a List Using Lambda Expression 

import java.util.Arrays;
import java.util.List;

public class CombineStrings {

    public static void main(String[] args) {

        List<String> words =
                Arrays.asList("Java", "Stream", "API", "Lambda");

        String result = words.stream()
                .reduce("", (a, b) -> a + " " + b);

        System.out.println("Combined String:");
        System.out.println(result.trim());
    }
}
