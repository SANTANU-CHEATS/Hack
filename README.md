import javax.swing.*;
import java.awt.*;
import java.text.SimpleDateFormat;
import java.util.Date;

public class DigitalClock extends JFrame {
    private JLabel timeLabel;

    public DigitalClock() {
        setTitle("Digital Clock");
        setSize(300, 100);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);
        setResizable(false);

        timeLabel = new JLabel("", SwingConstants.CENTER);
        timeLabel.setFont(new Font("Arial", Font.PLAIN, 48));
        add(timeLabel);

        // Timer to update the clock every second
        Timer timer = new Timer(1000, e -> updateClock());
        timer.start();

        updateClock(); // Initial update
    }

    private void updateClock() {
        String currentTime = new SimpleDateFormat("HH:mm:ss").format(new Date());
        timeLabel.setText(currentTime);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            DigitalClock clock = new DigitalClock();
            clock.setVisible(true);
        });
    }
}
