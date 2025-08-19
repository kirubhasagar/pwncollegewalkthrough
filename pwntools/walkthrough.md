lets us see how we can use pwntools to write an exploit and solve the challenges

challenge 0.0

from pwn import *

# Set architecture, os and log level
context(arch="amd64", os="linux", log_level="info")

# Load the ELF file and execute it as a new process.
challenge_path = "/challenge/pwntools-tutorials-level0.0"
p = process(challenge_path)

payload = b'pokemon\n'
# Send the payload after the string ":)\n###\n" is found.
p.sendafter(":)\n###\n", payload)

# Another way of doing things would be:
#payload = b'pokemon'
#p.sendlineafter(":)\n###\n", payload)

# Receive flag from the process
flag = p.recvline()
print(f"flag is: {flag}")

we can run this exploit to get the flag

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <errno.h>
#include"util.h"


void print_flag()
{
	char *p;
	FILE *fp;
	char flag[100];

	fp = fopen("/flag", "r");

	if (!fp) {
		perror("[-] fopen failed");
	}

	p = fgets(flag, sizeof(flag), fp);
	if (!p) {
		perror("[-] fgets failed");
		fclose(fp);
	}
	
	printf("%s", flag);

	fclose(fp);
}

int bypass_me(char *buf)
{	
	if (!strncmp(buf, "pokemon", 7)) {
		return 1;
	}
	
	return 0;
}

int main()
{
	char buffer[100];

	print_desc();

	fgets(buffer, sizeof(buffer), stdin);

	if (bypass_me(buffer)) {
		print_flag();
	} else {
		printf("You need to bypass some conditions to get the flag: \n");
		printf("Please refer to the source code to understand these conditions\n");	
	}

	print_exit();
	return 0;
}

Explanation:
   In bypass me function it checks whether the input is pokemon if it pokemon it triggers the print flag() function and we are able to get the flag