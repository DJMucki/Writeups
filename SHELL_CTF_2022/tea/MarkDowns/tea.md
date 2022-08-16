## Challenge Name: tea
##### Category: 
Reverse

##### Challenge Description: 
Let's reverse the way [shellpwn](https://ctftime.org/team/65394) makes tea.

##### Artifact Files:
* [tea binary](https://github.com/S-H-E-L-L/S.H.E.L.L-CTF-2022/blob/main/rev/tea/tea)

### Approach

**1. Reverse the binary with gihdra**

![img](https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/tea/Images/tea.png)

**2. Think about what the functions do**

![img](https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/tea/Images/boilWater.png)

**2.1 boilWater** reads the input and daves it into a global variable.

![img](https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/tea/Images/addSugar.png)

**2.2 addSugar** reorganizes the string so that all the characters in an odd index are in front and the even are at the back.

![img](https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/tea/Images/addTea.png)

**2.3 addTea** operates over the first half of the input and modifies it as follows: input[i] = input[i] - ( (i/2) * 3 )
the other half of the string suffers the following operation: input[i] = input[i] + (i/6)

![img](https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/tea/Images/addMilk.png)

**2.4 addMilk** divides the string into 3 parts
the first part ends at the first 5 excluding the 5,
the second part includes the 5 and ends at the next R excuding it and
the third part includes the R and the rest of the string

after which it appends the parts as follows:  **third + first + second**

![img](https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/tea/Images/strainAndServe.png)

**2.5 strainAndServe** compares the modified input with **R;crc75ihl`cNYe`]m%50gYhugow~34i**
if the strings are equal we get confirmation that we inputed the right flag.

**3. Reverse the tea making with python**

**4. Run the reverse**

### Reflections
<reflections ...>
  

---
[Back to home](https://github.com/DJMucki/SHELL_CTF_2022)