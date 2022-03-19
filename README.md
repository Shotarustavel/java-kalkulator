# java-kalkulator


package com.LTP.main;

import javax.swing.JFrame;
import  javax.swing.SwingUtilities;
import java.awt.*;


public class Start {
    private  JFrame window;

    public Start () {
        window = new JFrame( "კალკულატორი");
        window.setSize(325,350);
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
    private Font font = new Font("SanSerif", Font.BOLD,12);
    private JTextField output = new JTextField();
    private JButton backspace = new JButton("c"), equ = new JButton("=");
    private JButton plus = new JButton("+"), minus = new JButton("-"),multi = new JButton("*"), div = new JButton("/");
    private JButton perc = new JButton("%");
    private JButton mrc = new JButton("mr");
    private JButton fesv = new JButton("%");
    private JButton fl = new JButton(",");



    public Panel() {
        setLayout(null);

        perc.setBounds(250,70 , 50, 50);
        perc.setFont(font);
        add(perc);

        mrc.setBounds(250,130,50,50);
        mrc.setFont(font);
        add(mrc);

        fesv.setBounds(250,190,50,50);
        fesv.setFont(font);
        add(fesv);

        fl.setBounds(250,250,50,50);
        fl.setFont(font);
        add(fl);


        backspace.setBounds(10,250,50,50);
        backspace.setFont(font);
        add(backspace);

        equ.setBounds(130,250,50,50);
        equ.setFont(font);
        add(equ);


        plus.setBounds(190,70,50,50);
        plus.setFont(font);
        add(plus);



        minus.setBounds(190,130,50,50);
        minus.setFont(font);
        add(minus);

        multi.setBounds(190,190,50,50);
        multi.setFont(font);
        add(multi);

        div.setBounds(190,250,50,50);
        div.setFont(font);
        add(div);



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
        output.setBounds(10,10,290,50);
        output.setEditable(false);
        add(output);


        ActionListener l = (ActionEvent e) ->{
            JButton b = (JButton) e.getSource ();
            output.setText(output.getText() + b.getText());

        } ;
        for (JButton  b : numbers){
            b.addActionListener(l);


        }


    }

}
