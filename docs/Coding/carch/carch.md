# computer Architecture  

## Instruction level parallelism (ILP)  
1. one approach relies on hardware  
2. the other one is relying on the compiler.  

CPI = cycles per instructions 

## Memory Hieararchy

	cpu -> cache => Memory ->io devices
	250ps   1 ns     100ns      10ns
	500bytes  64KB    1GB        1TB. 
	
word
line/block = multiple words  

design decision : where blocks/lines can be placed in cache. 
	popular scheme is: set associative   
	set is a group of block in the cache.  
	a block is first mapped onto a set and the block can be placed anywhere in the set  
	if there are n block in a set then this is called n way set associative.  
	caching data that is read only easy.  
	but write is difficult 
		how can the data be ensured to be kept consistant. 
		1. Write Through - update in cache and memory both. 
		1. write back - write back to memory only occurs when it is about to be replaced. 
		both aproach can user write buffer to allow cache to proceed .  

	Miss Rate: 
	number of access missed from cache / total access attempt. 

Three C miss category: 
	1. Compulsory - first access must be from non cache.  
	1. Capacity - cache is full. it contains all the block needed for execution.  
	1. Conflict - if the block placement strategy is not fully associative.  

Some designer prefers Misses/ instruction  instead of miss rate.  

Avg memory access time = hit time + miss rate x miss penalty  

Processor can execute other instruction during the miss time.  

### how to improve the miss rate  
1. Large block size - use large block can cause miss penalty. Does larger block causes longer hit time?  
1. bigger cache - causes longer hit time  
1. Higher associativity - with the cost of hit time.  
1. Multilvl cache - reduce miss penalty  
	HT(L1) + MR x (HT(l2) + MR(L2) x Miss penalty(L2))  
1. give priority to read misses orver write (use write buffer)  
1.


###Questions  

1. What is the cache size for ADL CPU?  
1. what is the limitation to give extra large cache memory ? only cost and size?  
1. What is conflict miss.  