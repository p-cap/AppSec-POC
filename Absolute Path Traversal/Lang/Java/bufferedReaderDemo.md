## POC for BufferredReader Object instantiation
1. Create a directory named "parent"
2. Create a file named "pcap.txt"
3. Instantiate a new File object
   ```java
   // "../pcap.txt" is the absolute path traversal argument
   jshell> File file = new File("../pcap.txt")
   ```
   CP:
   ```java
   File file = new File("../pcap.txt")
   ```
4. Instantiate a new FileReaderObject with the File Object as its parameter
   ```java
   jshell> FileReader fileRead = new FileReader(file)
   fileRead ==> java.io.FileReader@7ca48474
   ```
   CP:
   ```java
   FileReader fileRead = new FileReader(file)
   ```
5. Instantiate a new BufferedReader object with FileReaderObject as its parameter
   ```java
   jshell> BufferedReader br = new BufferedReader(fileRead)
   br ==> java.io.BufferedReader@61a485d2
   ```
   CP:
   ```java
   BufferedReader br = new BufferedReader(fileRead)
   ```
6. Check the contents of br by calling the readLine() method
   ```java
   jshell> br.readLine()
   $4 ==> "Do you see me?"
   ```
   CP:
   ```java
   br.readLine()
   ```

## Attacker's perspective
If the source is NOT sanitized and validated, an attacker is able to traverse through the directory

### Reference
Class BufferedReader
https://docs.oracle.com/javase/7/docs/api/java/io/BufferedReader.html

### Legend:
CP = Copy/Paste
