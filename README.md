# Javacode11
package P11;

import java.io.*;
import java.time.*;
import java.time.format.*;
import java.util.Scanner;
public class S {
    public static void main(String[] args) {
        String fileName = "input_log.txt";
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
        Scanner scanner = new Scanner(System.in);

        try {
            PrintWriter writer = new PrintWriter(new FileWriter(fileName, true));
            System.out.println(" Type something (type 'exit' to quit):");

            while (true) {
                String input = scanner.nextLine();

                if (input.equalsIgnoreCase("exit")) {
                    System.out.println(" Exiting... All input saved to " + fileName);
                    break;
                }

                String timestamp = LocalDateTime.now().format(formatter);
                writer.println("[" + timestamp + "] " + input);
                writer.flush();

                System.out.println(" Logged: " + input);
            }

            writer.close();
            scanner.close();

        } catch (IOException e) {
            System.out.println(" Error writing to file: " + e.getMessage());
        }
    }
}
