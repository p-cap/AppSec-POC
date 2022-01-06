## POC for FileReader object Instantiation

### CONDITION 1: If the file does not exist
1. Create a directory named "parent"
2. ```cd parent```
3. Instantiate a new File object
   ```java
   // "../pcap.txt" is the absolute path traversal argument
   jshell> File file = new File("../pcap.txt")
   ```
   CP:
   ```java
   File file = new File("../pcap.txt")
   ```
4. Instantiate a filereader object using file object 
   ```java
   jshell> FileReader fileReader = new FileReader(file)
   |  Exception java.io.FileNotFoundException: ..\pcap.txt (The system cannot find the file specified)
   |        at FileInputStream.open0 (Native Method)
   |        at FileInputStream.open (FileInputStream.java:219)
   |        at FileInputStream.<init> (FileInputStream.java:157)
   |        at FileReader.<init> (FileReader.java:75)
   |        at (#2:1)
   ```
   CP:
   ```java
   FileReader fileReader = new FileReader(file)
   ```
## Observation
- If the file does not exists after instantiating the File object, FileReader raises an excpetion

### CONDITION 2: If the file exist
1. Create a directory named "parent"
2. Create a file named "pcap.txt"
3. ```cd parent```
4. repeat Step 3
5. Instantiate a filereader object using file object 
   ```java
   jshell>  FileReader fileReader = new FileReader(file)
   fileReader ==> java.io.FileReader@7ca48474
   ```
   CP:
   ```java
   FileReader fileReader = new FileReader(file)
   ```

## Attacker's perspective
If the source is NOT sanitized and validated, an attacker is able to traverse through the directory

### Reference
Class FileReader
https://docs.oracle.com/javase/7/docs/api/java/io/FileReader.html

### Legend:
CP = Copy/Paste
