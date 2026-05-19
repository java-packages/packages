//Client1

import java.io.*;
import java.net.*;
import java.util.Random;

public class Client1 {
    public static void main(String[] args) {
        try {
            System.out.println("=== CSMA Sender ===");
            Random r = new Random();

            for (int attempt = 1; attempt <= 5; attempt++) {
                System.out.println("\nAttempt : " + attempt);
                System.out.println("Checking channel...");

                try {
                    Socket s = new Socket("localhost", 5000);
                    System.out.println("Channel idle");

                    System.out.println("Waiting IFS...");
                    Thread.sleep(2000);

                    int backoff = r.nextInt(4) + 1;
                    System.out.println("Backoff time: " + backoff + " sec");
                    Thread.sleep(backoff * 1000);

                    DataOutputStream out = new DataOutputStream(s.getOutputStream());
                    out.writeUTF("Frame sent from Client1");
                    System.out.println("Message sent successfully");

                    out.close();
                    s.close();
                    break;

                } catch (Exception e) {
                    System.out.println("Channel busy, retrying...");
                    Thread.sleep(2000);
                }
            }

        } catch (Exception e) {
            System.out.println(e);

//Client2

import java.io.*;
import java.net.*;

public class Client2 {
    public static void main(String[] args) {
        try {
            ServerSocket ss = new ServerSocket(5000);
            System.out.println("=== CSMA Receiver ===");
            System.out.println("Waiting for sender...");

            while (true) {
                Socket s = ss.accept();

                DataInputStream in = new DataInputStream(s.getInputStream());
                String msg = in.readUTF();

                System.out.println("Received: " + msg);

                in.close();
                s.close();
            }

        } catch (Exception e) {
            System.out.println(e);
        }
    }
}
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
