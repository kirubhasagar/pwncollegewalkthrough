Let us dive into  the challenge 

challenge-1: connect
       
       connect with the ip and port number by using the nc command

       nc  <ip> port number

       that will give your flag

challenge-2: send

      connect to the remote machine and and just the send the msg that you want to send that will give the flag

challenge-3: shutdown
    
       Assume that you need to send a large amount of data to another device/machine, but you don't know in advance how much data you'll send. So, you can't use a specific word like "END" to signal the end of the message — because "END" might appear naturally in the data itself.

       Instead, a better approach is to signal the end of the data by closing the standard input (stdin). This can be done by pressing Ctrl+D, which sends an EOF (End of File) signal.

       However, Netcat doesn’t automatically close the network connection when stdin is closed. To handle this, we use the -N argument, which tells Netcat:

      "When stdin receives EOF (Ctrl+D), shut down the write side of the connection."

      This cleanly terminates the sending part of the connection while still allowing you to receive any response from the other side (if needed).

       So you can run the netcat command and press ctrl to get the flag

challenge-4: listen 
  
       just run the script at and then listen with help of the netcat command and you will get the flag

challenge-5: scan -1
 
       IN this challenge we need to simply used ping with a script in that network and get the ip which is up and connect with that ip with netcat and get the flag

challenge-6: scan-2
        
         just find the way how to get scan with network fast and connect with the i using netcat you will get the flag 