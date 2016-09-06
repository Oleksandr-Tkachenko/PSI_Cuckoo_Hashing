# Private Set Intersection (PSI)
###Cuckoo Hashing###
---
__Install:__
```
sudo make install
```
__Clean:__ 
```
sudo make clean
```

__Remove:__ 
```
sudo make remove
```

###Dependencies: 
* libglib2.0-dev 
* psi-utils
* libssl-dev

###Usage:
```
psi-cuckoo-hashing -1 16-Byte seed 1 -2 16-Byte seed 2 -3 16-Byte seed 3 -p path to dataset folder -b Double table size -t path to result folder -l Recursive deepness limit -e Exponent -r Integer read buffer size
```
