#
```

```

# PPC_Ez 2.beautify
```
題目敘述
幫我美化一下這句子

規則1 : 把所有 ' -_' 換成 ' '
規則2 : 把所有英⽂文字母換成小寫

nc 140.110.112.22 2401
```
## 初步測試看看連線與回應的行為
```
root@kali:~# nc 140.110.112.22 2401
===== Welcome to pretty shop =====
Can you help me beautify these sentences?
Rule 1 : change all ' -_' to ' '
Rule 2 : change all alphabet to lower case
----- Example -----
sentence : ThiS-iS_tEst tRY to BeautIfY_mE
answer : this is test try to beautify me
----- Now You Turn -----
sentence : MISs cOnTEmPT_NECk-dip dEFeAT-PAymEnt_innOCENT-pEn-cOnfRonTatION_AdMIraTIon_SChOOL-Trap-CIGarETte-owe hunTER
answer : 
```
## 解題思維
```

```

## 
```
#!/usr/bin/env python3
from pwn import *

r = remote('140.110.112.22', 20000)

r.recvlines(8)
r.recvuntil('sentence : ')
sentence = r.recvline().strip().decode()
ans = sentence.lower().replace('-', ' ').replace('_', ' ')
r.sendlineafter('answer : ', ans)

r.interactive()
```
