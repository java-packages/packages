//Server.java

import java.net.*;
import java.io.*;

public class Server {
    public static void main(String[] args) throws Exception {
        ServerSocket ss = new ServerSocket(5000);
        System.out.println("Server started");
        Socket s = ss.accept();
        System.out.println("Client connected");

        DataInputStream in = new DataInputStream(s.getInputStream());
        String msg = "";

        while (!msg.equals("Over")) {
            msg = in.readUTF();
            System.out.println(msg);
        }

        s.close();
        ss.close();
    }
}

//Client.java

import java.io.*;
import java.net.*;

public class Client {
    public static void main(String[] args) throws Exception {
        Socket s = new Socket("127.0.0.1", 5000);
        System.out.println("Connected");

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        DataOutputStream out = new DataOutputStream(s.getOutputStream());

        String msg = "";

        while (!msg.equals("Over")) {
            msg = br.readLine();
            out.writeUTF(msg);
        }

        br.close();
        out.close();
        s.close();
    }
}
