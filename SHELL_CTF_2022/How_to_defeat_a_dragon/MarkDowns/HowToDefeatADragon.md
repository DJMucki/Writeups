# How To defeat a dragon begginer reverse challenge

Reverse the given binary file with [Gihdra][gihdra_link]

![alt text][gihdra_decomp]

Take a look at the code and see the following

![alt text][gihdra_decomp_explained]

The programm takes the input and compares it with **0x10f2c** after which the **string** at local_78 is printed.

So possibly the **Flag** is local_78.

local_78 and following variables look like a struct of some kind.

We think it looks like this.

![alt text][flag_struct]

So we create a struct in [Gihdra][gihdra_link] and reverse the programm a bit more.

![alt text][gihdra_reversed]

Now we reversed as much as we can, lets run the program and get the output.

![alt text][vault_output]

The output **SHELLCTF{5348454c4c4354467b31355f523376337235316e675f333473793f7d}** looks weird.

We go to [CyberChef][cyber_chef_link] and paste the inner part of the output to run the **Magic operation**.

![alt text][cyber_chef]

The **Magic operation** says to try the **From Hex Operation**. 

![alt text][flag]

We can see the **Real Flag** is **SHELLCTF{15_R3v3r51ng_34sy?}**.

[gihdra_link]: https://ghidra-sre.org/ "gihdra link"
[cyber_chef_link]: https://gchq.github.io/CyberChef "cyber_chef_link"
[gihdra_reversed]: https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/.images/gihdra_reversed_explained.png "gihdra reversed"
[gihdra_decomp]: https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/.images/gihdra_decomp.png "gihdra decomp image"
[gihdra_decomp_explained]: https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/.images/gihdra_explained.png "gihdra decomp image explained"
[flag_struct]: https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/.images/flag_struct.png "flag struct" 
[vault_output]: https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/.images/vault_output.png "vault output" 
[cyber_chef]: https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/.images/CyberChef.png "cyber_chef" 
[flag]: https://github.com/DJMucki/Writeups/blob/main/SHELL_CTF_2022/.images/Flag.png "flag" 