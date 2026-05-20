//Java Program to Convert File Content to Uppercase Using File Handling

import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

public class UpperCaseFile {

    public static void main(String[] args) {

        try {

            FileReader fr = new FileReader("input.txt");
            FileWriter fw = new FileWriter("output.txt");

            int ch;

            while ((ch = fr.read()) != -1) {

                fw.write(Character.toUpperCase((char) ch));
            }

            fr.close();
            fw.close();

            System.out.println("Uppercase file created");

        } catch (IOException e) {

            System.out.println("File Error");
        }
    }
}
