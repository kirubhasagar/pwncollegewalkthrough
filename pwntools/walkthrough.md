lets us see how we can use pwntools to write an exploit and solve the challenges

challenge 0.0

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