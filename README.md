# java-kalkulator


package com.LTP.main;

import javax.swing.JFrame;
import  javax.swing.SwingUtilities;
import java.awt.*;


public class Start {
    private  JFrame window;

    public Start () {
        window = new JFrame( "კალკულატორი");
        window.setSize(280,350);
        window.add(new Panel());
        window.setLocationRelativeTo(null);
        window.setResizable(false);
        window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        window.setVisible(true);
    }


    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new Start();


            }


        });
    }
}








package com.LTP.main;


import  javax.swing.JPanel;
import javax.swing.JButton;
import java.awt.Font;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;
import javax.swing.JTextField;



public class Panel extends  JPanel{
    private  JButton numbers [] = new JButton[10];
    private Font font = new Font("SanSerif", Font.BOLD,20);
    private JTextField output = new JTextField();

    public Panel() {
        setLayout(null);

        numbers[0] = new JButton("0");
        numbers[0].setBounds(70,250,50,50);
        numbers[0].setFont(font);
        add(numbers[0]);
        for(int x = 0; x < 3 ; x++) {
            for (int y = 0;y < 3;y++) {
                numbers[y * 3 + x + 1] = new JButton((y * 3 + x + 1) + "");
                numbers[y * 3 + x + 1].setBounds(x * (50 + 10) + 10, y * (50 + 10) + 70, 50, 50);
                numbers[y * 3 + x + 1].setFont(font);
                add(numbers[y * 3 + x + 1]);
            }
        }
       output.setBounds(10,10,245,50);
        output.setEditable(false);
        add(output);


        ActionListener l = (ActionEvent e) ->{
            JButton b = (JButton) e.getSource ();
            output.setText(output.getText() + b.getText());
        } ;
        for (JButton b : numbers) {
            b.addActionListener(l);
        }

    }

}
