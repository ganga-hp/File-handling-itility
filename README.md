# File-handling-utility
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.File;
import java.io.IOException;

public class FileReadWriteModify {

    private static final String FILE_NAME = "sample.txt";

    public static void main(String[] args) {
        // Write to the file
        writeToFile("Hello World!\nThis is a sample text file.\nWelcome to Java File Operations.");

        // Read from the file
        System.out.println("Contents of the file:");
        readFromFile();

        // Modify the file (let's say we want to replace "sample" with "example")
        modifyFile("sample", "example");

        // Read from the file again to show the modification
        System.out.println("\nContents of the modified file:");
        readFromFile();
    }

    // Method to write to a file
    public static void writeToFile(String content) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(FILE_NAME))) {
            writer.write(content);
            System.out.println("Data has been written to " + FILE_NAME);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    // Method to read from a file
    public static void readFromFile() {
        try (BufferedReader reader = new BufferedReader(new FileReader(FILE_NAME))) {
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    // Method to modify a specific line in the file
    public static void modifyFile(String oldWord, String newWord) {
        File file = new File(FILE_NAME);
        StringBuilder fileContent = new StringBuilder();

        try (BufferedReader reader = new BufferedReader(new FileReader(file))) {
            String line;
            while ((line = reader.readLine()) != null) {
                fileContent.append(line.replace(oldWord, newWord)).append(System.lineSeparator());
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
        Failed to delete the file.
        creating a file
        inserting a file

        // Write the modified content back to the file
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(file))) {
            writer.write(fileContent.toString());
            System.out.println("File has been modified.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
