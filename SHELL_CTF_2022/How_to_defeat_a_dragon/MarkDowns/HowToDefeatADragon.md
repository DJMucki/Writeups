# How To defeat a dragon begginer reverse challenge

Reverse the given binary file with [Gihdra][https://ghidra-sre.org/]

![alt text][https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/How_to_defeat_a_dragon/images/gihdra_decomp.png]

Take a look at the code and see the following

![alt text][https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/How_to_defeat_a_dragon/images/gihdra_explained.png]

The programm takes the input and compares it with **0x10f2c** after which the **string** at local_78 is printed.

So possibly the **Flag** is local_78.

local_78 and following variables look like a struct of some kind.

We think it looks like this.

![alt text][https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/How_to_defeat_a_dragon/images/flag_struct.png]

So we create a struct in [Gihdra][https://ghidra-sre.org/] and reverse the programm a bit more.

![alt text][https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/How_to_defeat_a_dragon/images/gihdra_reversed_explained.png]

Now we reversed as much as we can, lets run the program and get the output.

![alt text][https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/How_to_defeat_a_dragon/images/vault_output.png]

The output **SHELLCTF{5348454c4c4354467b31355f523376337235316e675f333473793f7d}** looks weird.

We go to [CyberChef][https://gchq.github.io/CyberChef/] and paste the inner part of the output to run the **Magic operation**.

![alt text][https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/How_to_defeat_a_dragon/images/CyberChef.png]

The **Magic operation** says to try the **From Hex Operation**. 

![alt text][https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/How_to_defeat_a_dragon/images/Flag.png]

We can see the **Real Flag** is **SHELLCTF{15_R3v3r51ng_34sy?}**.

