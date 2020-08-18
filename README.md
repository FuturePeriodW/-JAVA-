# -JAVA-
package com.sign;

import com.database.*;
import java.awt.Font;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.SQLException;

import javax.swing.ImageIcon;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JPasswordField;
import javax.swing.JTextField;

public class sign extends JFrame {
	/* 身份登录识别部分 */

	public sign() {

		setTitle("小有登录界面");
		setLayout(null);
		setBounds(200, 200, 500, 400);
		setLocationRelativeTo(null);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
		JPanel c = (JPanel)getContentPane();//jp c
		
		
		
		
		/* 背景图片部分 */
		ImageIcon im = new ImageIcon("src/1.jpg");
		JLabel jl3 = new JLabel(im);
		jl3.setBounds(0, 0, im.getIconWidth(), im.getIconHeight());
		getLayeredPane().setLayout(null);
		
		
		JLabel jl1 = new JLabel("帐号:");


		Font font = new Font("楷体", Font.ITALIC, 13);
		jl1.setFont(font);
		JLabel jl2 = new JLabel("密码:");
		jl2.setFont(font);
		JTextField jt = new JTextField();
		
		JPasswordField jp = new JPasswordField();
		
		JButton jb = new JButton("登录");
		jb.setFont(font);
		jb.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				try {
					String password = new String(jp.getPassword());
					if ("".equals(jt.getText().trim()) | "".equals(password)) {
						new dialog(sign.this).setVisible(true);
					} else {
						if (data.getLogin(jt.getText(), password)) {
							new mainjm();
							dispose();
						} else {
							new dialog(sign.this).setVisible(true);
						}
					}

				} catch (SQLException e1) {
					// TODO Auto-generated catch block
					e1.printStackTrace();
				}
			}
		});

		jl1.setBounds(150, 250, 50, 20);
		jl2.setBounds(150, 280, 50, 20);
		
		jt.setBounds(180, 250, 150, 20);
		jp.setBounds(180, 280, 150, 20);
		jb.setBounds(350, 250, 60, 60);
		//jb.setBorderPainted(false);按钮边界不显示
		c.add(jl1);
		c.add(jl2);
		c.add(jt);
		c.add(jp);
		c.add(jb);
		c.setOpaque(false);//设置jpanle透明
		getLayeredPane().add(jl3,new Integer(Integer.MIN_VALUE));
		setVisible(true);
		validate();
	    repaint();
	}

}
