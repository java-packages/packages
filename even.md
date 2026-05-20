//Java Program to Filter Even Numbers from an Array List

import java.util.ArrayList;

public class EvenNumbers {

    public static void main(String[] args) {

        ArrayList<Integer> numbers = new ArrayList<>();

        numbers.add(10);
        numbers.add(15);
        numbers.add(20);
        numbers.add(25);
        numbers.add(30);

        System.out.println("Even Numbers:");

        for (int num : numbers) {

            if (num % 2 == 0) {
                System.out.println(num);
            }
        }
    }
}
