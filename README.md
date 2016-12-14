# Private Set Intersection (PSI)
###Cuckoo Hashing###


A memory-efficient implementation of the Cuckoo Hashing algorithm.

Elements are read from a file sequentially. Every read element is stored in a 
binary search tree, so that elements stay sorted based on their hash digests. 
After reaching some given threshold the tree will be dumped to the output file. 
The elements that caused collisions will be switchid with tree's elements and 
put back into the tree, where they will stay until next dumping routine.

While dealing with large inputs it is recommended to set the very high 
threshold value for the binary search tree size(read buffer size), so that by 
dumping its elements there will be a high probability of writing few elements 
into a single sector.

E.g.:
Cuckoo Hashing table size = 10^9 * 1.2
Sector size = 512 bytes
Element size in CH table = 19 bytes

Sectors in table = (table size * element size)/ sector size = ~44,5 * 10^6

So building the binary search tree of a size 100-200 *10^6 should be a good 
choice. However it is very memory-consuming, so 16 and more GB RAM size is 
recommended.

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
---
* libglib2.0-dev 
* psi-utils
* libssl-dev

###Usage:
---
_psi-cuckoo-hashing_ 
* -1 _16-Byte seed 1_ Hash seed
* -2 _16-Byte seed 2_ Hash seed
* -3 _16-Byte seed 3_ Hash seed
* -a _Path to file_ Path to the input file
* -p _Path destination_ Path to the output file
* -m _Double table size_ Size of hash table is calculated by multiplying 
number of elements by set value
* -l _Recursive deepness limit_ Limit value for putting elements into a stash.
* -r _read buffer size_ Size of the read buffer
* -f _"fixed table size(stronger than -m)"_ Fixed table size value. 
Stronger than table size multiplier
* -z _1_ Reduction of elements 16(19) to 10 bytes. Table additions are also 
removed, because there is no need to calculate bin addresses.

---
http://encrypto.de