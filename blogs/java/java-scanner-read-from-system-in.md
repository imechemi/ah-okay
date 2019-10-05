## Java Scanner not reading string after something ... 😬 

Facing NoElementException, or your scanner is not waiting for input after using it for reading other types? I had the same issue,
and it took almost 10 minutes complaining about why this simple I/O operation doesn't work. 


### Problem 

```java
Scanner scan = new Scanner(System.in);
int i = scan.nextInt();
String s = scan.nextLine();
scan.close();

System.out.println("String: " + s);
System.out.println("Int: " + i);
```

When I run the program, it does not wait for my second input. Program finishes running and prints an empty string at placeholder `s`

```sh
# Input 
23

# Output 
String: 
Int: 1
```




**What happens is that**, after `scan.nextInt()` assigns **23** to integer variable `i`. The scanner has a newline `\n` in its buffer 
which is waiting to be picked up by the next read. So when program reaches `scan.nextLine()`, it will read that newline `\n` from 
the buffer and run away without asking for the input that you want to provide. 


### Solution #1

Reset the scanner

```java
Scanner scan = new Scanner(System.in);
int i = scan.nextInt();
scan.nextLine();
scan.reset();  // Reset the scanner
String s = scan.nextLine();
scan.close();

System.out.println("String: " + s);
System.out.println("Int: " + i);
```

### Solution #2

Clear the buffer by reading and throwing it away.

```java
Scanner scan = new Scanner(System.in);
int i = scan.nextInt();
scan.nextLine();  // clear the buffer 
String s = scan.nextLine();
scan.close();

System.out.println("String: " + s);
System.out.println("Int: " + i);
```


### Solution #3
Use two different scanners 

```java
Scanner scan1 = new Scanner(System.in);
int i = scan1.nextInt();

Scanner scan2 = new Scanner(System.in);
String s = scan2.nextLine();
scan1.close();
scan2.close();

System.out.println("String: " + s);
System.out.println("Int: " + i);
```

🙃

