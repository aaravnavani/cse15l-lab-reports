# Lab Report 5 - Putting it All Together

## Part 1

### 1. The original post from a student with description

Hello,

I've been working on the ```ChatServer.java``` file, and I've noticed some weird behavior. Even if I don't pass in the parameter with `user=` or `message=`, the code still works and adds the message to the chat history and displays the message on the website. I am not really sure why this is, so I would appreciate it if someone could help me in sorting out this issue.

*insert screenshot here*


### 2. TA Response 

Hello,

Thanks for reaching out! Based on the information that you provided, the chat messages are still being added even if the parameters passed in the url are not being correct. This might be because of the way you are checking the `shouldBeUser[0]` and `shouldBeMessage[0]` variables. Try running this command: 


Could you also verify that you are verifying the value of `shouldBeUser[0]` and `shouldBeMessage[0]` before you set the `user` and `message` variables? Try running: 

```curl "localhost:8000/chat?test123=man&test456=hello"```

Let me know if you are able to fix the issue! 




