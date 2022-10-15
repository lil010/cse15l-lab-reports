# Week 3 Lab Report
## Part 1. Simplest Search Engine
Here is my code:
```
import java.io.IOException;
import java.net.URI;
import java.util.*;

class Handler implements URLHandler{

    ArrayList<String> searchList = new ArrayList<String>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Please add some items to the data base, or search for some items");
        } else {
            System.out.println("Path: " + url.getPath()); 
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    searchList.add(parameters[1]);
                    return String.format("item added!");
                }
            } else if(url.getPath().contains("/search")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    int timeAppearance = 0;
                    String result = "";
                    String space =" ";
                    for (int i = 0; i < searchList.size(); i++) {
                        if (searchList.get(i).contains(parameters[1])) {
                            timeAppearance++;
                            result = result.concat(searchList.get(i));
                            result = result.concat(space);
                        }
                    }
                    if (timeAppearance != 0) {
                        return String.format(result);
                    } else{
                        return String.format("Item Not Found!");
                    }
                }
            }
        return String.format("404 Not Found!");
        }
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

Adding apple: 

![image](week-3-lab-report/screenshot-w301.jpg)

This screenshot is using the method handleRequest. The process is activated by
```
if (url.getPath().contains("/add"))
```
a condition to check whether the url is called for adding items. Then, it called
```
String[] parameters = url.getQuery().split("=");
```
to separate the code after the add, which is "s" and the part after "=" apart. As it checked the left side of "=" being "s", it added the part after "=" to the array by activating the method:
```
searchList.add(parameters[1])
```
and return the statement "item added!"

Adding pineapple:
![image](week-3-lab-report/screenshot-w302.jpg)
This screenshot is using the method handleRequest. The process is activated by
```
if (url.getPath().contains("/add"))
```
a condition to check whether the url is called for adding items. Then, it called
```
String[] parameters = url.getQuery().split("=");
```
to separate the code after the add, which is "s" and the part after "=" apart. As it checked the left side of "=" being "s", it added the part after "=" to the array by activating the method:
```
searchList.add(parameters[1])
```
and return the statement "item added!"

Adding banana:
![image](week-3-lab-report/screenshot-w303.jpg)
This screenshot is using the method handleRequest. The process is activated by
```
if (url.getPath().contains("/add"))
```
a condition to check whether the url is called for adding items. Then, it called
```
String[] parameters = url.getQuery().split("=");
```
to separate the code after the add, which is "s" and the part after "=" apart. As it checked the left side of "=" being "s", it added the part after "=" to the array by activating the method:
```
searchList.add(parameters[1])
```
and return the statement "item added!"

Search words with "app":
![image](week-3-lab-report/screenshot-w304.jpg)
This screenshot is using the method handleRequest. The process is activated by
```
else if(url.getPath().contains("/search"))
```
a condition to check whether the url is called for searching items. Then, it called
```
String[] parameters = url.getQuery().split("=");
```
to separate the code after the add, which is "s" and the part after "=" apart. As it checked the left side of "=" being "s", it uses the for loop to search whether the element is in the word at certain index. If it is, it adds the word to a return list by using concat method. 

## Part 2 Bugs

Failure from ArrayExamples:

reversed method:

Failure input: {2, 3} as example; any array that has elements more than 1.

Symptom: The jUnit shows that the index at 0 is expected 3 but 0.

Bug: the array copies the new created 0 valued array to the original array. 


Failure from ListExamples:

merge method:

Failure input: {"apple", "mango", "pineapple"}, {"banana", "strawberry"}

Symptom: Out of Space Error

Bug: The increment in the third while loop in the code should be "index2 += 1" rather than "index1 += 1".
