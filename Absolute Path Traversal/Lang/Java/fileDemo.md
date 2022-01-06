## POC for File object Instantiation
1. Create two items:
   - file named "pcap.txt"
   - directory named "parent"
2. cd into parent directory
3. enter ```jshell``` in your terminal
4. Create a new File object 
   ```java
   // ../pcap.txt is argument performing the ABOSULTE PATH TRAVERSAL
   jshell> File file = new File("../pcap.txt");
   ```
5. To check if the file exists:
   ```java  
   jshell> file.exist();
   ```
## Observation
- When creating a new File object, the file DOES NOT have to exists within the server. No exception is raised
- Using the exist method will help you determine whether the file exists or not

## Attacker's perspective
If the source is NOT sanitized and validated, an attacker is able to traverse through the directory

### Reference
Class File
https://docs.oracle.com/javase/7/docs/api/java/io/File.html
