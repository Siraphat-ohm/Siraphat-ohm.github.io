---
title: SWU CTF Make Your Own Luck Write ups
published: 2025-07-01
description: 'write ups Zpecial-Challenge'
image: ''
tags: ["SWU CTF", "CTF"]
category: ''
draft: false 
lang: 'th'
---

# Introduction

write ups Zpecial-Challenge

ได้ไฟล์มาก็แตกไฟล์ก่อน

```bash
┌──(simon㉿simon)-[~/CTF/SWU_CTF/sp/Make_Your_Own_Luck]
└─$ unrar e Make_Your_Own_Luck.rar

UNRAR 7.11 freeware      Copyright (c) 1993-2025 Alexander Roshal


Extracting from Make_Your_Own_Luck.rar

Extracting  Make_Your_Own_Luck.py                                     OK
All OK
```

เปิดดูไฟล์

```python
import random

def reveal():
    cry = [88, 75, 68, 78, 26, 71, 68, 79, 89, 89, 73, 26, 68, 94, 88, 26, 70]
    random.seed()
    key = random.randint(1, 1000000)
    if key == 42:
        flag = ''.join(chr(c ^ (key % 256)) for c in cry)
        print(f"Your flag is: swu{{{flag}}}")
    else:
        print("No flag for you, try again!")

reveal()

#Write a short write-up for this challenge and send it to my LinkedIn: https://www.linkedin.com/in/chayawat-j/
#Only the first 3 hackers get 100 THB. Race you to the inbox!
#-- Chayawat Jeamprasertboon
```

จะเห็นว่า key hardcode ไว้

```python
key = 42
flag = ''.join(chr(c ^ (key % 256)) for c in cry)
```

```python
# sol.py

cry = [88, 75, 68, 78, 26, 71, 68, 79, 89, 89, 73, 26, 68, 94, 88, 26, 70]
key = 42

flag = ''.join(chr(c ^ (key % 256)) for c in cry)
print(f"Your flag is: swu{{{flag}}}")
```

```python
Your flag is: swu{rand0mnessc0ntr0l}
```