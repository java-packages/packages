//Java Program to Sort a List of String sUsing Lambda Expression

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class LambdaSorting {

    public static void main(String[] args) {

        List<String> names = new ArrayList<>();

        names.add("Thrisha");
        names.add("Wamiqa");
        names.add("Nazriya");
        names.add("Anaswara");

        System.out.println("Before Sorting:");
        System.out.println(names);

        Collections.sort(names, (a, b) -> a.compareTo(b));

        System.out.println("After Sorting:");
        System.out.println(names);
    }
}
