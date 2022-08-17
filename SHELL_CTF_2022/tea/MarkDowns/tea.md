# Challenge Name: tea
### Category: 
Reverse

### Challenge Description: 
Let's reverse the way [shellpwn](https://ctftime.org/team/65394) makes tea.

### Artifact Files:
* [tea binary](https://github.com/S-H-E-L-L/S.H.E.L.L-CTF-2022/blob/main/rev/tea/tea)

## Approach

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
'''python:
from pprint import pprint

ciphertext = "R;crc75ihl`cNYe`]m%50gYhugow~34i"

parts = ciphertext.split("5")
print(parts)
pool1 = []
pool2 = []
thirdandfirst1 = parts[0]
thirdandfirst2 = parts[0] + "5" + parts[1]
second1 = "5" + parts[1] + "5" + parts[2]
second2 = "5" + parts[2]


# reverse first part adding Milk
for x in range(len(thirdandfirst1)):
    x = x
    first = thirdandfirst1[x:]
    third = thirdandfirst1[:x]
    pool1.append(first + second1 + third)

for x in range(len(thirdandfirst2)):
    x = x
    first = thirdandfirst2[x:]
    third = thirdandfirst2[:x]
    pool2.append(first + second2 + third)

pool1.extend(pool2)
# pprint(pool1)
newpool = []
# reverse second part adding Tea
for cipher in pool1:
    count = 0
    # print(cipher)
    cipher = bytearray(bytes(cipher, "utf-8"))
    textlen = len(cipher) // 2
    print(len(cipher))

    first = cipher[:textlen]
    second = cipher[textlen:]
    tempstr = ""
    print(range(len(first)))
    for i in range(len(first)):
        shift = (count // 2) * 3
        # print(shift)
        first[i] = (first[i] + shift) % 255
        count += 1
    # print(count)
    # count += 1
    for i in range(len(second)):
        shift = count // 6
        # print(shift)
        second[i] = (second[i] - shift) % 255
        count += 1
    try:
        s1 = first.decode()
        # print(s1)
        s2 = second.decode()
        # print(s2)
        newpool.append(s1 + s2)
    except:
        for c in first:
            tempstr += chr(c)

        for c in second:
            tempstr += chr(c)
        newpool.append(tempstr)
        # print(tempstr)
        continue

# pprint(newpool)

# reverse third part adding Sugar

for elem in newpool:

    tempstr = ""
    lenelem = len(elem) // 2
    print(elem[lenelem:])
    print(elem[:lenelem])
    for chpair in zip(elem[lenelem:], elem[:lenelem]):
        tempstr += chpair[0]
        tempstr += chpair[1]
    print(tempstr)
# shellctf{T0_1nfiNi7y_4n?_y3kd}
'''

**4. Run the reverse**

## Reflections
<reflections ...>
  

---
[Back to home](https://github.com/DJMucki/SHELL_CTF_2022)
