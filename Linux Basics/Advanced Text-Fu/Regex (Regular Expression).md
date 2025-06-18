- Regular expressions are a powerful tool to do pattern based selection.
1.  Some Common Regex Patterns:1. **Beginning of a line with `^`**:
     - **Input (Bash command):**
       ```bash
       echo -e "sally sells seashells\nby the seashore" | grep ^by
       ```
     - **Output:**
       <span style = "color : red;" >by</span> the seashore
     
2. **End of a line with `$`**:
	- **Input**:
	```bash 
	echo -e "sally sells seashells\nby the seashore" | grep seashore$
	```
	- Output:
		by the <span style="color:red;">seashore</span>
		

3. **Matching any single character with `.`**:
	- Input:
		```bash
		echo -e "sally sells seashells\nby the seashore" | grep b.
		```
	- Output:
		<span style="color: red;">by</span> the seashore.

4. **Bracket Notation with `[]`**:
	- This can be a little tricky, brackets allow us to specify characters found within the bracket.
		- Input:
		```bash
		echo -e "sally sells seashells\nby the seashore" | grep s[eash]
		```
		- Output
			<span style="color: red;">sa</span>lly <span style="color: red;">se</span>lls sea<span style="color: red;">sh</span>ells by the <span style="color: red;">se</span>a<span style="color: red;">sh</span>ore
	- The previous anchor tag ^ when used in a bracket means anything except the characters within the bracket.
		- Input
		```bash
		echo -e "sally sells seashells\nby the seashore" | grep s[^e]
		```
		- Output
			<span style="color: red;">sa</span>lly sell<span style="color: red;">s</span> sea<span style="color: red;">sh</span>ells by the sea<span style="color: red;">sh</span>ore
	- Brackets can also use ranges to increase the amount of characters you want to use.
		- Input
		```bash
		echo -e "sally sells seashells\nby the seashore" | grep s[a-s]
		```
		- Output
			<span style="color: red;">sa</span>lly <span style="color: red;">se</span>lls <span style="color: red;">se</span>a<span style="color: red;">she</span>lls by the <span style="color: red;">se</span>a<span style="color: red;">sh</span>ore
	- Be careful though as brackets are case sensitive:
		- Input
		```bash
		echo -e "sally sells seashells\nby the seashore" | grep s[A-S]
		```
		- Output

