# FILE-HANDLING-UTILITY  

**COMPANY**: CODTECH IT SOLUTIONS

**NAME**: BHAMIDIPATI AKHILMITRA

**INTERN ID**:CT12GPD

**DOMAIN**: Java Programming

**BATCH DURATION**: DECEMBER 25TH,2024 TO FEBRUARY 25TH,2025

**MENTOR NAME**: NEELA SANTHOSH KUMAR

# ENTER THE DESCRIPTION OF TASK PERFORMED NOT LESS THAN 500 Words
A **file handling utility** in Java performs a series of tasks that allow for reading, writing, and manipulating files on the file system. Java provides a variety of classes and methods for managing files, from basic file input and output (I/O) operations to more advanced file manipulation. The following describes the primary tasks performed by a file handling utility in Java:

### 1. **File Creation and Deletion**
   - **Creating Files**: A Java file handling utility can create new files using the `File` class or `Files.createFile()` method from the `java.nio.file` package.
   - **Deleting Files**: Files can be deleted using `File.delete()` or `Files.delete()`.

   Example (Creating a file):
   ```java
   Path path = Paths.get("example.txt");
   Files.createFile(path);
   ```

### 2. **Reading Files**
   A file handling utility can read data from files in various formats (text, binary, etc.).
   - **Reading Text Files**: Java provides classes like `FileReader` and `BufferedReader` for reading text files line by line. `Files.readAllLines()` from `java.nio.file` is another convenient method.
   - **Reading Binary Files**: For binary files, classes like `FileInputStream` and `BufferedInputStream` are used.

   Example (Reading a text file):
   ```java
   List<String> lines = Files.readAllLines(Paths.get("example.txt"));
   for (String line : lines) {
       System.out.println(line);
   }
   ```

### 3. **Writing to Files**
   Writing data to files is one of the core tasks of a file handling utility.
   - **Writing Text Files**: Java allows writing text data using `FileWriter` or `BufferedWriter`. You can also use `Files.write()` to write a list of strings or byte data to a file.
   - **Writing Binary Files**: `FileOutputStream` or `BufferedOutputStream` is used for writing binary data.

   Example (Writing to a file):
   ```java
   List<String> data = Arrays.asList("Line 1", "Line 2", "Line 3");
   Files.write(Paths.get("example.txt"), data);
   ```

### 4. **File Copying, Moving, and Renaming**
   - **Copying Files**: The `Files.copy()` method allows copying files from one location to another.
   - **Moving/Renaming Files**: You can move or rename a file using the `Files.move()` method.

   Example (Copying a file):
   ```java
   Path source = Paths.get("source.txt");
   Path destination = Paths.get("destination.txt");
   Files.copy(source, destination, StandardCopyOption.REPLACE_EXISTING);
   ```

### 5. **Checking File Properties**
   The utility can check various properties of files, such as:
   - **Exists**: Check if a file exists using `Files.exists()`.
   - **Is Directory**: Verify if a file is a directory using `Files.isDirectory()`.
   - **File Size**: Retrieve the file size using `Files.size()`.

   Example (Check file existence):
   ```java
   boolean exists = Files.exists(Paths.get("example.txt"));
   ```

### 6. **Directory Operations**
   - **Listing Files**: You can list files in a directory using `Files.list()` or `File.listFiles()`.
   - **Creating Directories**: New directories can be created with `Files.createDirectory()` or `File.mkdir()`.
   - **Deleting Directories**: Directories can be deleted using `Files.delete()` (if empty) or `Files.walkFileTree()` for non-empty directories.

   Example (Listing files in a directory):
   ```java
   try (Stream<Path> paths = Files.walk(Paths.get("mydir"))) {
       paths.filter(Files::isRegularFile)
            .forEach(System.out::println);
   }
   ```

### 7. **Error Handling and Exceptions**
   File handling operations can result in various exceptions such as `IOException`, `FileNotFoundException`, or `AccessDeniedException`. A file handling utility should handle these exceptions properly to ensure the application runs smoothly.

   Example (Handling exceptions):
   ```java
   try {
       Files.readAllLines(Paths.get("nonexistent.txt"));
   } catch (IOException e) {
       System.out.println("Error: " + e.getMessage());
   }
   ```

In summary, a file handling utility in Java is responsible for tasks such as file creation, reading and writing data, copying, moving, renaming files, checking file properties, and performing directory operations. Proper error handling is also critical to ensure smooth file management.
