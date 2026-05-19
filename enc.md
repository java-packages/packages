import java.io.*;
import java.security.*;
import javax.crypto.Cipher;
import java.util.Base64;

public class RSAFileEncryption {
    public static void main(String[] args) throws Exception {

        KeyPairGenerator keyGen = KeyPairGenerator.getInstance("RSA");
        keyGen.initialize(2048);

        KeyPair pair = keyGen.generateKeyPair();
        PublicKey publicKey = pair.getPublic();
        PrivateKey privateKey = pair.getPrivate();

        File file = new File("input.txt");
        FileInputStream fis = new FileInputStream(file);

        byte[] data = new byte[(int) file.length()];
        fis.read(data);
        fis.close();

        Cipher cipher = Cipher.getInstance("RSA");
        cipher.init(Cipher.ENCRYPT_MODE, publicKey);

        byte[] encryptedData = cipher.doFinal(data);

        FileOutputStream fos = new FileOutputStream("encrypted.txt");
        fos.write(Base64.getEncoder().encode(encryptedData));
        fos.close();

        System.out.println("File Encrypted Successfully!");

        cipher.init(Cipher.DECRYPT_MODE, privateKey);

        byte[] decryptedData = cipher.doFinal(encryptedData);

        FileOutputStream fos2 = new FileOutputStream("decrypted.txt");
        fos2.write(decryptedData);
        fos2.close();

        System.out.println("File Decrypted Successfully!");
    }
}
