import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

/**
 * This is a Stack GUI application that performs pop, push, and peek operations. I added the peek, size,  
 * and clear operations and modified some of the events such as implementing actionListener.
 * 
 * Code is based on Exercises from:
 * @author Java Foundations
 *http://studenthome.sunyocc.edu/~pagelj/csc112/outline.html
 */
public class StackGUI extends JPanel
{
    private JButton pushButton; //adds push button
    private JButton popButton;  //adds pop button
    private JButton peekButton;  //adds peek button
    private JButton clearButton; //adds clear button
    private JButton sizeButton;  //adds size button
    private JTextArea currentStack;
    private JLabel inputLabel;
    private JTextField currentInput;
    private JTextArea currentAction;
    private JPanel panel;
    private LinkedStack<String> myStack = new LinkedStack<String>();

    /**
     * Sets up the GUI.
     */
    public StackGUI()
    {
        //adding the buttons and implementing actionListeners
        pushButton = new JButton("Push");
        pushButton.addActionListener(new PushListener());
        popButton = new JButton("Pop");
        popButton.addActionListener(new PopListener());
        peekButton = new JButton("Peek");
        peekButton.addActionListener(new PeekListener());
        clearButton = new JButton("Clear");
        clearButton.addActionListener(new ClearListener());
        sizeButton = new JButton("Size");
        sizeButton.addActionListener(new SizeListener());

        inputLabel = new JLabel("Add to stack: ");
        currentInput = new JTextField(18);
        currentInput.setEditable(true);
        currentStack = new JTextArea(6, 20);
        currentStack.setMargin(new Insets(5,5,5,5));
        currentStack.setEditable(false);
        currentAction = new JTextArea(3,20);
        currentAction.setMargin(new Insets(5,5,5,5));
        currentAction.setEditable(false);
        currentAction.setText("");

        panel = new JPanel();
        panel.add(inputLabel);
        panel.add(currentInput);
        //to add the stack operations button on the panel
        panel.add(pushButton);
        panel.add(popButton);
        panel.add(peekButton);
        panel.add(clearButton);
        panel.add(sizeButton);

        setLayout(new BorderLayout());
        add(new JScrollPane(currentStack), BorderLayout.NORTH);
        add(panel, BorderLayout.CENTER);
        add(new JScrollPane(currentAction), BorderLayout.SOUTH);
        setBorder(BorderFactory.createEmptyBorder(20, 20, 20, 20));
    }

    /**
     * Creates and displays the main application frame.
     */
    public void display()
    {
        JFrame frame = new JFrame("Stack GUI Application Demo");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setContentPane(this);

        frame.pack();
        frame.setVisible(true);
    }

    /**
     * Represents an action listener for the push button.
     */
    private class PushListener implements ActionListener
    {
        /**
         * Adds the contents of the user entry text field to the 
         * top of this stack.
         * @param event incoming event
         */
        public void actionPerformed (ActionEvent event)
        {
            String toPush = currentInput.getText();
            if (toPush.length() !=0)
            {
                myStack.push(toPush);
                currentAction.append("\"" + toPush+"\"" + " was pushed onto " +
                    "the stack.\n");
                currentStack.setText(myStack.toString());
                currentStack.setCaretPosition( 0 ); // forces scroll up
                currentInput.setText(null); // clears input field
            }
            else{
                currentAction.append("Cannot push empty data.\n");
            }
        }
    }

    /**
     * Represents an action listener for the pop button.
     */
    private class PopListener implements ActionListener
    {
        /**
         * removes the element at the 
         * top of this stack.
         * @param event incoming event
         */
        public void actionPerformed (ActionEvent event)
        {
            if (! myStack.isEmpty())
            {
                String popped = myStack.pop();
                currentAction.append("\"" + popped +"\"" + " was popped off " +
                    "the stack.\n");    
                currentStack.setText(myStack.toString());
                currentStack.setCaretPosition( 0 );
                currentInput.setText(null);
            }
            else{
                currentAction.append("Cannot pop from an empty stack.\n");
            }
        }
    }
    
    /**
     * Represents an action listener for the peek button.
     */
    private class PeekListener implements ActionListener
    {
        /**
         * returns the element at the 
         * top of this stack.
         * @param event incoming event
         */
        public void actionPerformed (ActionEvent event)
        {
            if (! myStack.isEmpty())
            {
                String peeked = myStack.peek();
                currentAction.append("\"" + peeked +"\"" + " is on the top of " +
                    "the stack.\n");    
                currentStack.setText(myStack.toString());
                currentStack.setCaretPosition( 0 );
                currentInput.setText(null);
            }
            else{
                currentAction.append("This is an empty stack. Cannot perform peek.\n");
            }
        }
    }
    
    
    /**
     * Represents an action listener for the clear button.
     */
    private class ClearListener implements ActionListener
    {
        /**
         * clears the stack.
         * @param event incoming event
         */
        public void actionPerformed (ActionEvent event)
        {
            if (! myStack.isEmpty())
            {
                currentAction.append("The stack has been cleared.\n");    
                currentStack.setText(" ");
                currentStack.setCaretPosition( 0 );
                currentInput.setText(null);
            } else if( myStack.isEmpty()){
                 currentAction.append("The stack is already empty.\n");
            }
            else{
                currentAction.append("This is an empty stack.\n");
            }
        }
    }
    
    /**
     * Represents an action listener for the size button.
     */
    private class SizeListener implements ActionListener
    {
        /**
         * returns the size of the stack/number of elements in the stack
         * @param event incoming event
         */
        public void actionPerformed (ActionEvent event)
        {
            if (! myStack.isEmpty())
            {
                Integer size = myStack.size();
                currentAction.append("There are " + size + " items in the stack.\n");    
                currentStack.setText(myStack.toString());
                currentStack.setCaretPosition( 0 );
                currentInput.setText(null);
            }
            else{
                currentAction.append("This is an empty stack.\n");
            }
        }
    }
}
