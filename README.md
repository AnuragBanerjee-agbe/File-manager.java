import java.io.*;
import java.util.Scanner;

public class FileManager {

    // Write content to a text file
    public static void writeToFile(String fileName, String content) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(fileName))) {
            writer.write(content);
            System.out.println("✅ FILE HAS BEEN WRITTEN SUCCESSFULLY.");
        } catch (IOException e) {
            System.out.println("❌ ERROR WHILE WRITING TO FILE: " + e.getMessage());
        }
    }

    // Read content from a text file
    public static void readFromFile(String fileName) {
        try (BufferedReader reader = new BufferedReader(new FileReader(fileName))) {
            System.out.println("📄 FILE CONTENT:");
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println("  " + line);
            }
        } catch (IOException e) {
            System.out.println("❌ ERROR WHILE READING THE FILE: " + e.getMessage());
        }
    }

    // Append content to a text file
    public static void appendToFile(String fileName, String content) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(fileName, true))) {
            writer.newLine();
            writer.write(content);
            System.out.println("✏️ FILE HAS BEEN MODIFIED SUCCESSFULLY.");
        } catch (IOException e) {
            System.out.println("❌ ERROR WHILE MODIFYING FILE: " + e.getMessage());
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String fileName = "Internship_Task_2.txt";  // 🔄 UPDATED FILE NAME

        System.out.println("\n📁 SIMPLE FILE OPERATIONS IN JAVA");
        System.out.println("1. WRITE TO FILE");
        System.out.println("2. READ FROM FILE");
        System.out.println("3. APPEND TO FILE");
        System.out.print("👉 ENTER YOUR CHOICE: ");
        int choice = sc.nextInt();
        sc.nextLine(); // consume newline

        switch (choice) {
            case 1:
                System.out.print("✍️ ENTER TEXT TO WRITE: ");
                String writeText = sc.nextLine();
                writeToFile(fileName, writeText);
                break;

            case 2:
                readFromFile(fileName);
                break;

            case 3:
                System.out.print("➕ ENTER TEXT TO APPEND: ");
                String appendText = sc.nextLine();
                appendToFile(fileName, appendText);
                break;

            default:
                System.out.println("❗ INVALID CHOICE. PLEASE TRY AGAIN.");
        }

        sc.close();
    }
}
