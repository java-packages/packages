//Java Program to Build a Calculator Using Swing 


import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Calculator extends JFrame implements ActionListener {

    JTextField t1, t2, result;
    JButton add, sub, mul, div;

    Calculator() {

        t1 = new JTextField();
        t2 = new JTextField();
        result = new JTextField();

        add = new JButton("+");
        sub = new JButton("-");
        mul = new JButton("*");
        div = new JButton("/");

        setLayout(new GridLayout(5, 2));

        add(new JLabel("First Number"));
        add(t1);

        add(new JLabel("Second Number"));
        add(t2);

        add(add);
        add(sub);
        add(mul);
        add(div);

        add(new JLabel("Result"));
        add(result);

        add.addActionListener(this);
        sub.addActionListener(this);
        mul.addActionListener(this);
        div.addActionListener(this);

        setSize(300, 200);
        setVisible(true);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }

    public void actionPerformed(ActionEvent e) {

        double n1 = Double.parseDouble(t1.getText());
        double n2 = Double.parseDouble(t2.getText());
        double res = 0;

        if (e.getSource() == add)
            res = n1 + n2;

        else if (e.getSource() == sub)
            res = n1 - n2;

        else if (e.getSource() == mul)
            res = n1 * n2;

        else if (e.getSource() == div)
            res = n1 / n2;

        result.setText(String.valueOf(res));
    }

    public static void main(String[] args) {

        new Calculator();
    }
}
