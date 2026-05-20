//Java Program to Display a Digital Watch Using Swing 

import javax.swing.*;
import java.awt.*;
import java.text.SimpleDateFormat;
import java.util.Date;

public class DigitalClock extends JFrame {

    JLabel clock;

    DigitalClock() {

        clock = new JLabel();

        clock.setFont(new Font("Arial", Font.BOLD, 40));
        clock.setHorizontalAlignment(SwingConstants.CENTER);

        add(clock);

        setSize(400, 200);
        setVisible(true);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        Timer t = new Timer(1000, e -> updateClock());
        t.start();

        updateClock();
    }

    void updateClock() {

        SimpleDateFormat sdf =
                new SimpleDateFormat("HH:mm:ss");

        clock.setText(sdf.format(new Date()));
    }

    public static void main(String[] args) {

        new DigitalClock();
    }
}
