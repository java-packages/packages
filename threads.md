//Java Program to Print Messages Alternately Using Multiple Threads

class Shared {

    boolean first = true;

    synchronized void printFirst() {

        for (int i = 1; i <= 5; i++) {

            while (!first) {
                try {
                    wait();
                } catch (Exception e) {
                }
            }

            System.out.println("Thread 1 : " + i);

            first = false;
            notify();
        }
    }

    synchronized void printSecond() {

        for (int i = 1; i <= 5; i++) {

            while (first) {
                try {
                    wait();
                } catch (Exception e) {
                }
            }

            System.out.println("Thread 2 : " + i);

            first = true;
            notify();
        }
    }
}

class Thread1 extends Thread {

    Shared s;

    Thread1(Shared s) {
        this.s = s;
    }

    public void run() {
        s.printFirst();
    }
}

class Thread2 extends Thread {

    Shared s;

    Thread2(Shared s) {
        this.s = s;
    }

    public void run() {
        s.printSecond();
    }
}

public class ThreadSynchronization {

    public static void main(String[] args) {

        Shared s = new Shared();

        Thread1 t1 = new Thread1(s);
        Thread2 t2 = new Thread2(s);

        t1.start();
        t2.start();
    }
}
