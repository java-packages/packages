import javax.net.ssl.*;
import java.net.URL;
import java.security.cert.Certificate;

public class TLSHandshakeDemo {
    public static void main(String[] args) throws Exception {
        String httpsURL = "https://www.google.com";

        URL url = new URL(httpsURL);
        HttpsURLConnection connection =
                (HttpsURLConnection) url.openConnection();

        connection.connect();

        System.out.println("Response Code: " + connection.getResponseCode());
        System.out.println("Cipher Suite: " + connection.getCipherSuite());

        System.out.println("\nServer Certificates:");
        Certificate[] certs = connection.getServerCertificates();

        for (Certificate cert : certs) {
            System.out.println("Certificate Type: " + cert.getType());
            System.out.println("Public Key: " + cert.getPublicKey());
            System.out.println("-----------------------------------");
        }

        connection.disconnect();
    }
}
