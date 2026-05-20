//File Reading Using File Reader with Exception Handling

import java.io.FileReader;
import java.io.IOException;

public class FileReadExample {

    public static void main(String[] args) {

        try {

            FileReader fr = new FileReader("filewrite.txt");

            int ch;

            System.out.println("File Contents:");

            while ((ch = fr.read()) != -1) {
                System.out.print((char) ch);
            }

            fr.close();

        } catch (IOException e) {

            System.out.println("File Error");
        }
    }
}
