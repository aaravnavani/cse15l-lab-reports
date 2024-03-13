# Lab Report 5 - Putting it All Together

## Part 1

### 1. The original post from a student with description

Hello,

I've been working on the ```ChatServer.java``` file, and I've noticed some weird behavior. Even if I don't pass in the parameter with `user=` or `message=`, the code still works and adds the message to the chat history and displays the message on the website. I am running this ```run.sh``` file on the terminal using ```bash run.sh```:

```
#!/bin/bash
javac ChatServer.java Server.java
java ChatServer 8000
```

I am not really sure why this is, so I would appreciate it if someone could help me in sorting out this issue.


### 2. TA Response 

Hello,

Thanks for reaching out! Based on the information that you provided, the chat messages are still being added even if the parameters passed in the url are not being correct. This might be because of the way you are checking the `shouldBeUser[0]` and `shouldBeMessage[0]` variables. Try running this command: 


Could you also verify that you are verifying the value of `shouldBeUser[0]` and `shouldBeMessage[0]` before you set the `user` and `message` variables? Try running: 

```curl "localhost:8000/chat?test123=man&test456=hello"```

Let me know if you are able to fix the issue! 

### 3.Clear Description of Bug & Screenshot 

Screenshot: 

The bug is that the student does not check whether ```shouldBeUser[0]``` is equal to ```user``` and if ```shouldBeMessage[0]``` is equal to ```message```. 

### 4. All the Information 

#### The file & directory structure needed

```
├── ChatHistoryReader.java
├── ChatServer.java
├── HandlerTests.java
└── Server.java
```

#### The contents of each file before fixing the bug

Contents of ```ChatServer.java```:

```
import java.io.IOException;
import java.net.URI;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;

class ChatHandler implements URLHandler {
  String chatHistory = "";

  public String handleRequest(URI url) {
    // expect /chat?user=<name>&message=<string>
    if (url.getPath().equals("/chat")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeUser = params[0].split("=");
      String[] shouldBeMessage = params[1].split("=");
      String user = shouldBeUser[1];
      String message = shouldBeMessage[1];
      this.chatHistory += user + ": " + message + "\n\n";
      return this.chatHistory;
    }
    // expect /retrieve-history?file=<name>
    else if (url.getPath().equals("/retrieve-history")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeFile = params[0].split("=");
      if (shouldBeFile[0].equals("file")) {
        String fileName = shouldBeFile[1];
        // String fileName = shouldBeFileName[0]; // bug4: should be shouldBeFile[1]
        ChatHistoryReader reader = new ChatHistoryReader();
        try {
          String[] contents = reader.readFileAsArray("chathistory/" + fileName);
          for (String line : contents) {
            this.chatHistory += line + "\n\n";
          }
        } catch (IOException e) {
          System.err.println("Error reading file: " + e.getMessage());
        }
      }
      return this.chatHistory;
    }
    // expect /save?name=<name>
    else if (url.getPath().equals("/save")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeFileName = params[0].split("=");
      if (shouldBeFileName[0].equals("name")) {
        File directory = new File("chathistory");
        File file = new File(directory, shouldBeFileName[1]);

        try (BufferedWriter writer = new BufferedWriter(new FileWriter(file))) {
          writer.write(this.chatHistory);
          return "Data written to " + shouldBeFileName[1] + "in 'chat-history' folder.";
        } catch (IOException e) {
          e.printStackTrace();
          return "Error: Something wrong happen during file save, check StackTrace";
        }
      }
    }

    return this.chatHistory;
  }
}

class ChatServer {
  public static void main(String[] args) throws IOException {
    int port = Integer.parseInt(args[0]);
    Server.start(port, new ChatHandler());
  }
}
```

#### A description of what to edit to fix the bug

The student must add this line: 

```if (shouldBeUser[0].equals("user") && shouldBeMessage[0].equals("message")) {```

at the very start of the ```handleRequest``` method to verify the ```shouldBeUser[0]``` and ```shouldBeMessage[0]``` variables.  

The student also needs to add: 

```
else {
        return "Invalid parameters: " + String.join("&", params);
      }
```

right after the ```return this.chatHistory``` line so that if invalid parameters are given, the user is told. 

Here is the updated code:

```
import java.io.IOException;
import java.net.URI;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;

class ChatHandler implements URLHandler {
  String chatHistory = "";

  public String handleRequest(URI url) {

    // expect /chat?user=<name>&message=<string>
    if (url.getPath().equals("/chat")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeUser = params[0].split("=");
      String[] shouldBeMessage = params[1].split("=");
      if (shouldBeUser[0].equals("user") && shouldBeMessage[0].equals("message")) {
        String user = shouldBeUser[1];
        String message = shouldBeMessage[1];
        this.chatHistory += user + ": " + message + "\n\n";
        return this.chatHistory;
      } else {
        return "Invalid parameters: " + String.join("&", params);
      }
    }
    // expect /retrieve-history?file=<name>
    else if (url.getPath().equals("/retrieve-history")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeFile = params[0].split("=");
      if (shouldBeFile[0].equals("file")) {
        String fileName = shouldBeFile[1];
        ChatHistoryReader reader = new ChatHistoryReader();
        try {
          String[] contents = reader.readFileAsArray("chathistory/" + fileName);
          for (String line : contents) {
            this.chatHistory += line + "\n\n";
          }
        } catch (IOException e) {
          System.err.println("Error reading file: " + e.getMessage());
        }
      }
      return this.chatHistory;
    }
    // expect /save?name=<name>
    else if (url.getPath().equals("/save")) {
      String[] params = url.getQuery().split("&");
      String[] shouldBeFileName = params[0].split("=");
      if (shouldBeFileName[0].equals("name")) {
        File directory = new File("chathistory");
        File file = new File(directory, shouldBeFileName[1]);

        try (BufferedWriter writer = new BufferedWriter(new FileWriter(file))) {
          writer.write(this.chatHistory);
          return "Data written to " + shouldBeFileName[1] + "in 'chat-history' folder.";
        } catch (IOException e) {
          e.printStackTrace();
          return "Error: Something wrong happen during file save, check StackTrace";
        }
      }
    }

    return this.chatHistory;
  }
}

class ChatServer {
  public static void main(String[] args) throws IOException {
    int port = Integer.parseInt(args[0]);
    Server.start(port, new ChatHandler());
  }
}
```

## Part 2: Reflection

Some cool things that I learned was how ```grep``` works and how it is really powerful in fidning files based on a specific criteria. I feel like this would be really useful in industry when dealing with a large codebase. Another thing that I found really useful was using ```curl```. I was able to use ```curl``` for testing some api calls and it worked really well and was easy enough for me to do, without having to set up a whole new python or java file. Overall, I learned a lot and I will be using the stuff that I learned in class when working on various projects as well as in industry. 
