//Java Program to Reverse a List Using a Generic Method

import java.util.ArrayList;
import java.util.List;

public class GenericReverse {

    static <T> List<T> reverseList(List<T> list) {

        List<T> rev = new ArrayList<>();

        for (int i = list.size() - 1; i >= 0; i--) {
            rev.add(list.get(i));
        }

        return rev;
    }

    public static void main(String[] args) {

        List<Integer> nums = new ArrayList<>();

        nums.add(10);
        nums.add(20);
        nums.add(30);
        nums.add(40);

        System.out.println("Original List: " + nums);
        System.out.println("Reversed List: " + reverseList(nums));
    }
}
