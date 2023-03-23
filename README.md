## 0x19. C - Stacks, Queues - LIFO, FIFO
![MAKE TEA NOT LOVE](https://pbs.twimg.com/media/CFYYWy6UEAE9Ow-.png)
### Resources
**Read or watch:**
- [Google](https://intranet.alxswe.com/rltoken/tn1X658KGumYYq_szFJI5w)
- [How do I use extern to share variables between source files in C?](https://intranet.alxswe.com/rltoken/0KVWTdE8xXy__jUfBfakCw)
- [Stacks and Queues in C](https://intranet.alxswe.com/rltoken/udmomL4F4mF630D2Z-ltqg)
- [Stack operations](https://intranet.alxswe.com/rltoken/fj_-SJXW-pWxgAnstsARoQ)
- [Queue operations](https://intranet.alxswe.com/rltoken/6Y_GVoIH_rV45xd7w0a9FA)
### More Info
#### Data structures
Please use the following data structures for this project. Don’t forget to include them in your header file.
```
/**
 * struct stack_s - doubly linked list representation of a stack (or queue)
 * @n: integer
 * @prev: points to the previous element of the stack (or queue)
 * @next: points to the next element of the stack (or queue)
 *
 * Description: doubly linked list node structure
 * for stack, queues, LIFO, FIFO
 */
typedef struct stack_s
{
	int n;
	struct stack_s *prev;
	struct stack_s *next;
} stack_t;
```
```
/**
 * struct instruction_s - opcode and its function
 * @opcode: the opcode
 * @f: function to handle the opcode
 *
 * Description: opcode and its function
 * for stack, queues, LIFO, FIFO
 */
typedef struct instruction_s
{
	char *opcode;
	void (*f)(stack_t **stack, unsigned int line_number);
} instruction_t;
```
### Compilation & Output
- Your code will be compiled this way:
`gcc -Wall -Werror -Wextra -pedantic -std=c89 *.c -o monty`
- Any output must be printed on `stdout`
- Any error message must be printed on `stderr`
	- [Here is a link to a GitHub repository](https://intranet.alxswe.com/rltoken/Cv-FVD5dZn3814FM4WkBPQ) that could help you making sure your errors are printed on `stderr`
### The Monty language
Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it. The goal of this project is to create an interpreter for Monty ByteCodes files.
**Monty byte code files**
Files containing Monty byte codes usually have the .m extension. Most of the industry uses this standard but it is not required by the specification of the language. There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument:
```
julien@ubuntu:~/monty$ cat -e bytecodes/000.m
push 0$
push 1$
push 2$
  push 3$
  					pall    $
push 4$
	push 5    $
		push    6        $
pall$
julien@ubuntu:~/monty$
```
Monty byte code files can contain blank lines (empty or made of spaces only, and any additional text after the opcode or its required argument is not taken into account:
```
julien@ubuntu:~/monty$ cat -e bytecodes/001.m
push 0 Push 0 onto the stack$
push 1 Push 1 onto the stack$
$
push 2$
  push 3$
  				pall    $
$
$
						$
push 4$
$
	push 5    $
		push    6        $
$
pall This is the end of our program. Monty is awesome!$
julien@ubuntu:~/monty$
```
#### The monty program
- Usage: `monty file`
	- where `file` is the path to the file containing Monty byte code
- If the user does not give any file or more than one argument to your program, print the error message `USAGE: monty file`, followed by a new line, and exit with the status `EXIT_FAILURE`
- If, for any reason, it’s not possible to open the file, print the error message `Error: Can't open file <file>`, followed by a new line, and exit with the status `EXIT_FAILURE`
	- where `<file>` is the name of the file
- If the file contains an invalid instruction, print the error message `L<line_number>: unknown instruction <opcode>`, followed by a new line, and exit with the status `EXIT_FAILURE`
	- where is the line number where the instruction appears.
	- Line numbers always start at 1
- The monty program runs the bytecodes line by line and stop if either:
	- it executed properly every line of the file
	- it finds an error in the file
	- an error occured
- If you can’t malloc anymore, print the error message `Error: malloc failed`, followed by a new line, and exit with status `EXIT_FAILURE`.
- You have to use `malloc` and `free` and are not allowed to use any other function from `man malloc` (realloc, calloc, …)

## Tasks
### 0. push, pall
- `pall.c` - The opcode `pall` prints all the values on the stack, starting from the top of the stack.
- `push.c` - The opcode `push` pushes an element to the stack.
### 1. pint
- `pint.c` - prints the value at the top of the stack, followed by a new line.
### 2. pop
- `pop.c` - removes the top element of the stack.
### 3. swap
- `swap.c` - swaps the top two elements of the stack.
### 4. add
- `add.c` - adds the top two elements of the stack.
### 5. nop
- `nop.c` - doesn’t do anything.
### 6. sub
- `sub.c` - subtracts the top element of the stack from the second top element of the stack.
### 7. div
- `div.c` - divides the second top element of the stack by the top element of the stack.
### 8. mul
- `mul.c` - multiplies the second top element of the stack with the top element of the stack.
### 9. mod
- `mod.c` - computes the rest of the division of the second top element of the stack by the top element of the stack.
### 10. comments
- When the first non-space character of a line is `#`, treat this line as a comment (don’t do anything).
### 11. pchar
- `pchar.c` - prints the char at the top of the stack, followed by a new line.
### 12. pstr
- `pstr.c` - prints the string starting at the top of the stack, followed by a new line.
### 13. rotl
- `rotl.c` - rotates the stack to the top.
### 14. rotr
- `rotr.c` - rotates the stack to the bottom.
### 15. stack, queue
- `stack.c` - sets the format of the data to a stack (LIFO). This is the default behavior of the program.
- `queue.c` - sets the format of the data to a queue (FIFO).
### 16. Brainf*ck
- `bf` - a Brainf*ck script that prints `School`, followed by a new line.
### 17. Add two digits
- `1001-add.bf` - Adds two digits given by the user.
### 18. Multiplication
- `1002-mul.bf` - Multiplies two digits given by the user.
### 19. Multiplication level up
- `1003-mul.bf` - Read the two digits from stdin, multiply them, and print the result, followed by a new line.
