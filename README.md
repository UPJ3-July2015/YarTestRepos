package net.makl.chat.gui;

import java.awt.Color;
import java.awt.ComponentOrientation;
import java.awt.Container;
import java.awt.Frame;
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JList;
import javax.swing.JMenu;
import javax.swing.JMenuBar;
import javax.swing.JMenuItem;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextPane;
import javax.swing.SwingUtilities;

public class GUIchat {
	
	public static void main(String[] args) {
		SwingUtilities.invokeLater(new Runnable() {
			public void run() {
				new GUIchat().createAndShowGui();

			}
		});

	}

	private void createAndShowGui() {
		JFrame frame = new JFrame("GUI Socket Chat 0.001");
		JMenuBar menuBar = new JMenuBar();

		frame.setJMenuBar(menuBar);
		
		JMenu mnFile = new JMenu("File");
		JMenuItem fileSave = new JMenuItem("Save history...");
		mnFile.add(fileSave);		
		JMenuItem fileExit = new JMenuItem("Exit");		
		mnFile.add(fileExit);
		menuBar.add(mnFile);

		fileExit.addActionListener(new ActionListener() {
			@Override
			public void actionPerformed(ActionEvent e) {
				System.exit(1);
				
			}
		});
		
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		addComponentsToPane(frame.getContentPane());
		frame.pack();
		frame.setSize(800, 800);
		frame.setLocation(300, 300);
		frame.setVisible(true);
	}

	private static void addComponentsToPane(Container pane) {

		pane.setComponentOrientation(ComponentOrientation.LEFT_TO_RIGHT);
		pane.setLayout(new GridBagLayout());
		
		JTextArea chatPane = new JTextArea();
		final GridBagConstraints chatPaneConstraints = new GridBagConstraints();
		chatPaneConstraints.gridx = 0;
		chatPaneConstraints.gridy = 0;
		chatPaneConstraints.gridwidth = 4;
		chatPaneConstraints.gridheight = 3;
		chatPaneConstraints.weightx = 0.7;
		chatPaneConstraints.weighty = 1;
		chatPaneConstraints.fill = GridBagConstraints.BOTH;
		chatPane.setBackground(Color.GRAY);
		chatPane.setEditable(false);
		chatPane.setText("Waiting users conect...		");
		
		

		pane.add(chatPane, chatPaneConstraints);
		
		JList<String> memberList = new JList<String>(new String[] {"One", "Two","John"});
		final GridBagConstraints memberListConstraints = new GridBagConstraints();
		memberListConstraints.gridx = 4;
		memberListConstraints.gridy = 0;
		memberListConstraints.gridwidth = 2;
		memberListConstraints.gridheight = 3;
		memberListConstraints.weightx = 0.3;
		memberListConstraints.weighty = 1;
		memberListConstraints.fill = GridBagConstraints.BOTH;
		pane.add(memberList, memberListConstraints);
		
		
		
		JTextArea editPane = new JTextArea();
		final GridBagConstraints editPaneConstraints = new GridBagConstraints();
		editPaneConstraints.gridx = 0;
		editPaneConstraints.gridy = 5;
		editPaneConstraints.gridwidth = 4;
		editPaneConstraints.gridheight = 1;
		
		editPaneConstraints.fill = GridBagConstraints.HORIZONTAL;
		editPane.setBackground(Color.WHITE);
		editPane.setEditable(true);
		editPane.setText("Type...");
		pane.add(editPane, editPaneConstraints);


		JButton button = new JButton("Send");
		final GridBagConstraints sendButtonConstraints = new GridBagConstraints();		
		sendButtonConstraints.gridx = 5;   
		sendButtonConstraints.gridwidth = 1;
		sendButtonConstraints.gridy = 5;

		sendButtonConstraints.fill = GridBagConstraints.HORIZONTAL;
		pane.add(button, sendButtonConstraints);
		
		

		
		
		
	}
	
	

}
