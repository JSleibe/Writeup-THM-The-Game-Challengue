# Writeup-THM-The-Game-Challengue
# TryHackMe - The Game (Challenge)  
*Writeup by Juan Salvador Sleibe*

---

## Challenge Information
- Name: The Game  
- File Provided: `Tetrix.exe-1741979048280.zip` → `Tetrix.exe`  
- Objective: Analyze the binary and recover the hidden flag.

---

## Analysis
The challenge provided a ZIP file containing a Windows executable named `Tetrix.exe`.  
Rather than executing it directly, I opted for static analysis. This approach is safer and often reveals valuable information without running potentially harmful code.  

The first tool I used was `strings`.  
- `strings` scans a binary and extracts sequences of printable characters.  
- Many times, binaries contain embedded text, debug information, or even sensitive data.  
- This is particularly useful in CTF challenges, as flags are often left in plain text.  

To refine the search, I combined it with `grep`.  
- `grep` filters input and outputs only the lines that match a given pattern.  
- Since TryHackMe flags usually follow the format `THM{...}`, I searched specifically for the keyword `THM`.  

The command used was:

strings Tetrix.exe | grep THM
The output revealed the hidden flag inside the binary:
THM{I_CAN_READ_IT_ALL}
Lessons Learned;
Static analysis is a powerful first step before attempting reverse engineering or dynamic execution.
strings can quickly expose hidden information, making it an essential tool for initial triage.
grep is effective to filter large outputs and focus only on relevant patterns, such as flag formats.
Even files that appear complex, like an executable game, may contain the solution in plain text.


This challenge demonstrates that sometimes the simplest tools yield the fastest results.
By combining strings and grep, I was able to locate and recover the flag without running the program or performing deep reverse engineering.
The flag obtained was:
THM{I_CAN_READ_IT_ALL}
