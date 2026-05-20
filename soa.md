//Sum of the array using Multi-threading 


class SumThread extends Thread {

    int[] arr;
    int start, end, sum = 0;

    SumThread(int[] a, int s, int e) {
        arr = a;
        start = s;
        end = e;
    }

    public void run() {

        for (int i = start; i < end; i++) {
            sum += arr[i];
        }
    }
}

public class MultiThreadArraySum {

    public static void main(String[] args) {

        int[] arr = {10, 20, 30, 40, 50, 60};

        int mid = arr.length / 2;

        SumThread t1 = new SumThread(arr, 0, mid);
        SumThread t2 = new SumThread(arr, mid, arr.length);

        t1.start();
        t2.start();

        try {
            t1.join();
            t2.join();
        } catch (InterruptedException e) {
            System.out.println("Error");
        }

        System.out.println("Total Sum = " + (t1.sum + t2.sum));
    }
}
