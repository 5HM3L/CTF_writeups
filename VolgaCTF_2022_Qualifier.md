# VolgaCTF 2022 Qualifier 
 ##  Communicating Exponents
 
Для решения понадобится [RsaCtfTool.py](https://github.com/Ganapati/RsaCtfTool)
 
Запускаем:
```shell
python3 RsaCtfTool.py --publickey rsa_pub.pem --private
```

Вывод программы будет слудеющим:
```shell
[ * ] Attack success with boneh_dufree method ! 

Private key :
-----BEGIN RSA PRIVATE KEY-----
MIIEYwIBAAKCAQB/FnriJTdilGFdUXGnfR+fsE3s00cO5xWIJPxNL5meti/v6w58
38M0UkRCndWlSvw7CXwSRxaGbfuf5Z3msETvK0zCtHKKsu5BPIk+2WoNNdcL4LBD
Ay3QhXD6+ZbYTqQee/UrHISCiMhrJc99ENfLReZo/HBvtpDi+G2qtKwV/ZpPUHa3
g6K5H/ceb9ev4ieO3t4LuIe7FjNGagrKbkQYPYXzPr6nYZYKRnKKaFZUIk1CUsB4
xKkQ17eYHRl3Du+vtEmrowxhA3072Vsg3hDDZKR2BPagrxxapCqRTYoW8xrKIiPU
/Q758pvFk/GyLHw3jHbIGM62n4tbXNvG4DW7AoIBAAQJBLuD2VV5UHWCfyeHZk08
MgswbFSu8pWeJ4rFhWK0W8ewGnOr7PWU0pbeinRqZ0IUuVs+/kCncaHa7Mquvlgq
Q385qlmJIpYzQogGv6Jk5lCgRcZTJlh1IGMEMBIsio6wBpPmwv7ypiemEgNpiBOC
m28khTOpDvRKJ6Rav9mW7OSC99eC9gtnxSiHlHbYZqcAr2YSGeXH2Pzod5hjXOGo
0H6LNzrghj8x7K1weDkriPC5OPBhDzTwAYcLeMD4LnWHKyWVJeMsiSXitlMT8VYt
q7arDTb4WZ4AWb4RRYFVEu1m8WxaP1Qbzdr8R3lEWzOeaKztfjw1LaoqAKopUNkC
QhBUM2RxZBYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAASQKBgQDM/wAgeO9HNbvH/38Dk3grboCw2wBmzBaG
HadD3niAAhp8R7wNA8m7dWhm5XMa7LKRE9q/iJhvQB0MZI2/98IAI1E3JTpEC5M6
854hvgy/WAMTHRtGvnPDlBTQvqyyriuNgxtTo58bnVwqSu3Q8mMNALN8lypt4a8m
uonMo+Tv2QKBgQCetTKXXeN3SOCxlNHCltm0TVwyOvo1c0bn/nT/MXGhGunc8mVL
wZcfqQGes/uTd15Unkjy/Dtu39g0jeQS5PQ1yyxyA412yA0hwgVulDMhrQbSWNVU
gspyFgr/jHxG9m92Lt/4zGHr34mwzbsZ09RwvhAv1B3kH4TQbWjGG4DpswJCEFQz
ZHFkFgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAABJAkIQVDNkcWQWAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEkCgYEAnim/9AiZrGDu
inIFmrAX0XOIjhKpHB5AOks2gt5FIC2r2eMYrY9Dncbq/fERC7xPHfFD7S1RXe+W
tUyT9rNoJH3zhcMp96pTp8dh5AeQyq6goO7Jq+PobpubdlzKZdyOyiMj2UGJ3XlN
gq2eZRCtX/L1kSHXf0bp0oBLKlWZqQM=
-----END RSA PRIVATE KEY-----
```
Сохраняем полученный приватный ключ в файл `priv.key`

Для шифрования сообщения использовалась утилита `openssl`:
```shell
openssl rsautl -encrypt -inkey rsa_pub.pem -in flag.txt -out flag.enc 
```

Значит для расшифрования сообщения воспользуемся следующей командой:
```shell
openssl rsautl -decrypt -inkey priv.key -in flag.enc -out flag.txt ; cat flag.txt
```

`VolgaCTF{wh0_r34lly_us3_sm4ll_d_v4lu3}`
