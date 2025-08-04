<small>walktrough for access control</small>



level 1:

![alt text](./image.png)

The hacker user has a read permission to the file flag . so we can simply read the flag and see 

level 2:

![alt text](image-1.png)

The hacker group has a read permission to the file flag . so we can simply read the flag and see

level 3:

![alt text](image-2.png)

we can see the hacker user has become the owner of the file 

so we can add the read permission to the file by chmod and we cat and see the /flag file

level 4:

![alt text](image-3.png)

In this challenge the suid is set to the binary /bin/cat we can use that binary to see the /flag file

/bin/cat /flag

level 5:

![alt text](image-4.png)

In this challenge the suid is set for the binary /bin/cp so we can copy the content in the file /flag  with the help of that into another file and we can cat and see the file 

In this challenge when we cp the file the directly from the flag  and adding the contents to the new file we cna t able to cat and see the file 

so we need to fist create file and then we need to copy the flag file contents to that file

Level 6:

![alt text](image-5.png)

In this challenge we want to add the user to the group and we also knew the passwd for the group 

so we can use the command

           newgrp <group-name>
           
           and enter the passwd

           this will not permanently add the user to the group but it will tempporarily add the user to that group

           so we can now cat the /flag and see now flag


Challenge-7:

![alt text](image-6.png)

In this challenge we can switch the user and we can cat and see the flag because read permission is set for the other user.

Challenge-8:

![alt text](image-7.png)

In this challenge the user has a permission to read the file . so we need to switch to that user and we cna able to cat that file and see but here the user is the owner of the file

Challenge-9:

![alt text](image-9.png)

In this challenge we can see that there is user and group name same . so the user be in that group so we can switch to that user and cat the flag

challenge-10:

![alt text](image-10.png)

In this challenge there are 10 users in different groups . so we have to find the user in a particular group and we need to switch to that user and cat and see the file  .so instead of using the groups command separately we can use a simple script to automate the task and find the crct user in that grp and solve it

#!/bin/bash

group="groupname"                   

users="user1 user2 user3"

for user in $users; do
    if groups "$user" | grep -qw "$group"; then
        echo "$user is in $group"
    fi
done
