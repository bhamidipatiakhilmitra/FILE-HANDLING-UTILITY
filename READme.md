import java.io.*;
import java.util.Scanner;

public class FileOperations {

    // Method to write data to a text file
    public static void writeToFile(String filename, String data) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(filename))) {
            writer.write(data);  // Write data to the file
            System.out.println("Data has been written to the file.");
        } catch (IOException e) {
            System.err.println("An error occurred while writing to the file: " + e.getMessage());
        }
    }

    // Method to read data from a text file
    public static void readFromFile(String filename) {
        try (BufferedReader reader = new BufferedReader(new FileReader(filename))) {
            String line;
            System.out.println("Reading from the file:");
            while ((line = reader.readLine()) != null) {
                System.out.println(line);  // Print each line of the file
            }
        } catch (IOException e) {
            System.err.println("An error occurred while reading the file: " + e.getMessage());
        }
    }

    // Method to append data to an existing text file
    public static void appendToFile(String filename, String data) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(filename, true))) {
            writer.write(data);  // Append data to the file
            writer.newLine();  // Add a new line after appending
            System.out.println("Data has been appended to the file.");
        } catch (IOException e) {
            System.err.println("An error occurred while appending to the file: " + e.getMessage());
        }
    }

    // Method to modify a specific line in the text file
    public static void modifyFile(String filename, String oldLine, String newLine) {
        File tempFile = new File("temp.txt");
        try (BufferedReader reader = new BufferedReader(new FileReader(filename));
             BufferedWriter writer = new BufferedWriter(new FileWriter(tempFile))) {

            String line;
            boolean lineReplaced = false;

            // Read each line and replace the old line with the new one
            while ((line = reader.readLine()) != null) {
                if (line.equals(oldLine)) {
                    writer.write(newLine);  // Write the modified line
                    writer.newLine();
                    lineReplaced = true;
                } else {
                    writer.write(line);  // Write the original line
                    writer.newLine();
                }
            }

            // If the line was replaced, rename the temp file to the original file
            if (lineReplaced) {
                if (filename.delete()) {
                    tempFile.renameTo(new File(filename));
                    System.out.println("File has been modified.");
                } else {
                    System.err.println("Failed to delete the original file.");
                }
            } else {
                System.out.println("The specified line was not found.");
            }

        } catch (IOException e) {
            System.err.println("An error occurred while modifying the file: " + e.getMessage());
        }
    }

    // Main method to demonstrate file operations
    public static void main(String[] args) {
        String filename = "example.txt";
        String data = "Hello, this is the first line of the file.\nWelcome to Java file operations!";
        String appendData = "This is additional text being appended to the file.";
        String oldLine = "Welcome to Java file operations!";
        String newLine = "Java file operations are fun and powerful.";

        // Step 1: Write to file
        writeToFile(filename, data);

        // Step 2: Read from file
        readFromFile(filename);

        // Step 3: Append to file
        appendToFile(filename, appendData);

        // Step 4: Read file again after appending
        readFromFile(filename);

        // Step 5: Modify the file (replace a specific line)
        modifyFile(filename, oldLine, newLine);

        // Step 6: Read the file after modification
        readFromFile(filename);
    }
}
