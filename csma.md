// CLIENT 1
import java.io.*;
import java.net.*;

public class Client1 {

    public static void main(String[] args) {

        try {
            System.out.println("============ Client 1 ===============");

            Client1 cli = new Client1();

            int R = 0;
            boolean bln = false;

            for (int k = 1; k <= 15; k++) {

                System.out.println("\nAttempt : " + k);

                // Check channel idle
                System.out.println("Is Channel idle?");

                int i = 0;

                while (true) {

                    System.out.print(++i + " ");

                    if (cli.isIdle()) {

                        System.out.println("\nChannel idle");

                        // Wait IFS time
                        System.out.println("Wait IFS time 5000");
                        Thread.sleep(5000);

                        // Check still idle
                        System.out.println("Is still idle?");

                        if (cli.isIdle()) {

                            System.out.println("Still idle");

                            // Random number selection
                            R = (int) (Math.pow(2, k) - 1);

                            System.out.println("Selected Random number : " + R);

                            System.out.println("Waiting for R slot time : " + (R * 1000));

                            // Wait R slot
                            Thread.sleep(R * 1000);

                            // Send frame
                            System.out.println("Message sent");

                            // Wait timeout
                            System.out.println("Wait for timeout : 10000");

                            Thread.sleep(10000);

                            // ACK check
                            if (cli.isIdle()) {

                                System.out.println("Ack received");

                                bln = true;

                                break;

                            } else {

                                System.out.println("Ack not received");

                                break;
                            }

                        } else {

                            System.out.println("Busy, goes to channel idle check");
                        }
                    }

                    Thread.sleep(1000);
                }

                if (bln == true) {
                    break;
                }
            }

        } catch (Exception e) {

            System.out.println(e);
        }
    }

    boolean isIdle() {

        try {

            Socket soc = new Socket("localhost", 137);

            soc.close();

            return true;

        } catch (Exception e) {

            return false;
        }
    }
}


// CLIENT 2
import java.io.*;
import java.net.*;

public class Client2 {

    public static void main(String[] args) {

        try {

            System.out.println("============ Client 2 ===============");

            ServerSocket ss = new ServerSocket(137);

            while (true) {

                System.out.println("Waiting for connection...");

                Socket s = ss.accept();

                System.out.println("Connected");

                s.close();
            }

        } catch (Exception e) {

            System.out.println(e);
        }
    }
}

LAST SATHYA
import java.util.*;

public class CSMACA{
public static void main(String a[]){

Random r=new Random();

int c1=r.nextInt(10);
int c2=r.nextInt(10);

System.out.println("Client 1 waits "+c1+" ms");
System.out.println("Client 2 waits "+c2+" ms");

if(c1<c2)
System.out.println("Client 1 transmits first");
else if(c2<c1)
System.out.println("Client 2 transmits first");
else
System.out.println("Collision Occurred");
}}
