lets us see how we can use pwntools to write an exploit and solve the challenges

# challenge 0.0

# Exploit

from pwn import *

context(arch="amd64", os="linux", log_level="info")

challenge_path = "/challenge/pwntools-tutorials-level0.0"

p = process(challenge_path)

payload = b'pokemon\n'

p.sendafter(":)\n###\n", payload)

flag = p.recvline()

print(f"flag is: {flag}")

Explanation:
   In bypass me function it checks whether the input is pokemon if it pokemon it triggers the print flag() function and we are able to get the flag


# challenge 1.0 

# exploit

from pwn import *

context(arch="amd64", os="linux", log_level="info")


challenge_path = "/challenge/pwntools-tutorials-level1.0"
p = process(challenge_path)


payload = p32(0xdeadbeef)
p.sendlineafter(":)\n###\n", payload)


flag = p.recvline()
print(f"flag is: {flag}")

Explanation:

In this challenge we need to match with 0xdeadbeef value which is compared in the bypass me function and it triggers the print_flag function

so why p32 -> converts into little endian format

when we analyze the binary by the file command we can see that LSB -> so it is little endian format

and when we send the payload we get the flag

