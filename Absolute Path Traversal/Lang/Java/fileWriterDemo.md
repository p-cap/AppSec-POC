## POC for FileWriter object Instantiation

### CONDITION: The file may or may not exists
1. Create a directory named "parent"
2. ```cd parent```
3. Instantiate a new FileWriter object
```java
// this is where the Absolute Traversal can potentially occur
jshell> FileWriter writer = new FileWriter("../see_me", false)
writer ==> java.io.FileWriter@153f5a29
```
 CP:
```java
FileWriter writer = new FileWriter("../see_me", false)
```
4. Call the write method to add some contents to the newly created file
```java
jshell> writer.write("I am added to the file system!!!!!!!!!  :-)")
```
CP:
```java
writer.write("I am added to the file system!!!!!!!!!  :-)")
```
5. Close the write object
```java
jshell> writer.close()
```
CP:
```java
writer.close()
```
5. Look for the newly created file with the contents to verify that it was created
```cmd
PS C:\....> ls


    Directory: 


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----          1/6/2022   4:16 AM                parent
-a----          1/6/2022   8:08 AM             16 pcap.txt
-a----          1/6/2022   8:22 AM             43 see_me


PS C:\...> cat .\see_me
I am added to the file system!!!!!!!!!  :-)
```

## Observation
- Whether the file exists or not, FileWriter will create the file

## Attacker's perspective
If the source is NOT sanitized and validated, an attacker is able to create a new file or traverse via existing file and read from it.

### Reference
Class FileWriter
https://docs.oracle.com/javase/7/docs/api/java/io/FileWriter.html

### Legend:
CP = Copy/Paste
