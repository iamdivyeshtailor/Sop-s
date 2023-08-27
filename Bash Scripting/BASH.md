###  Introduction
![[Screen Shot 2022-11-19 at 12.30.07 AM.png]]

- This is How any Device works 
- Its has a Hardware in which all resources are there like (CPU & RAM and Processor)
- and Kernal interact with all hardware
- but we throught shell we can tell kerval what to do


### What is Shell Scripting

- Shell Scripting consist of set of commands to perform a task
- All the commands executes sequentially
- some task like file manipultion ,progam execution, user interection, automation of task etc can be done.

### Types of Shell

- Bourne Shell (sh)
- Bourne Again Shell (Bash)
- Korn Shell
- C shell
- TCsh Shell

- To which bash you are using. Just this command in Terminal  
```bash
echo $0
```

### Scripting Format

- Before start bash scipt mention this
- This defines which bash you are using
```bash
#!/bin/bash
```
 - after that start righting commands
 - after competing script. assiged execute permission
```bash
chmod +x filename
```
- and then run using this command
```bash
./filename
```

### Variable's in Shell

- To Define Variable
```bash
var_name=value
var_name=$(hostname)
```
- use variable in script
```bash
echo$var_name
```
