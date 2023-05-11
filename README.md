# A simple bash script for showing disassembly of symbols for ELF64 files
This simple scirpt is a wrapper around objdump, and shows disassembly only to the symbol that is specified in the command line arguments. 

## Usage
```bash
./disas <mode> <symbol name> <filename>
```
example:
```bash
./disas d main ./a.out
```
or 

```bash
./disas d _start ./a.out
`
for symbol main, shows output like this:

```bash
disassembing "main" from /a.out 
    1139:	55                   	push   %rbp
    113a:	48 89 e5             	mov    %rsp,%rbp
    113d:	48 83 ec 20          	sub    $0x20,%rsp
    1141:	c7 45 e0 01 00 00 00 	movl   $0x1,-0x20(%rbp)
    1148:	c7 45 e4 02 00 00 00 	movl   $0x2,-0x1c(%rbp)
    114f:	c7 45 e8 03 00 00 00 	movl   $0x3,-0x18(%rbp)
    1156:	c7 45 ec 04 00 00 00 	movl   $0x4,-0x14(%rbp)
    115d:	48 8d 05 a0 0e 00 00 	lea    0xea0(%rip),%rax        # 2004 <_IO_stdin_used+0x4>
    1164:	48 89 45 f0          	mov    %rax,-0x10(%rbp)
    1168:	48 8d 05 97 0e 00 00 	lea    0xe97(%rip),%rax        # 2006 <_IO_stdin_used+0x6>
    116f:	48 89 45 f8          	mov    %rax,-0x8(%rbp)
    1173:	8b 45 e0             	mov    -0x20(%rbp),%eax
    1176:	89 c6                	mov    %eax,%esi
    1178:	48 8d 05 89 0e 00 00 	lea    0xe89(%rip),%rax        # 2008 <_IO_stdin_used+0x8>
    117f:	48 89 c7             	mov    %rax,%rdi
    1182:	b8 00 00 00 00       	mov    $0x0,%eax
    1187:	e8 a4 fe ff ff       	call   1030 <printf@plt>
    118c:	48 8b 45 f0          	mov    -0x10(%rbp),%rax
    1190:	48 89 c7             	mov    %rax,%rdi
    1193:	b8 00 00 00 00       	mov    $0x0,%eax
    1198:	e8 93 fe ff ff       	call   1030 <printf@plt>
    119d:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
    11a1:	48 89 c7             	mov    %rax,%rdi
    11a4:	b8 00 00 00 00       	mov    $0x0,%eax
    11a9:	e8 82 fe ff ff       	call   1030 <printf@plt>
    11ae:	b8 00 00 00 00       	mov    $0x0,%eax
    11b3:	c9                   	leave
    11b4:	c3                   	ret

Disassembly of section .fini:
```
