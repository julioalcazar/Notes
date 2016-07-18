###__No-Temp Swap__  
X = X ^ Y  
Y = X ^ Y  
X = X ^ Y  
  
Performance  
*  This swap method will fail if X and Y point to the same address.  
*  On modern CPU architectures, the XOR technique can be slower than using a temporary variable to do swapping. One reason is that modern CPUs strive to execute instructions in parallel via instruction pipelines. In the XOR technique, the inputs to each operation depend on the results of the previous operation, so they must be executed in strictly sequential order, negating any benefits of instruction-level parallelism.
  
---
  
###__No-Branch Minimum__  
Answer = Y ^ ((X ^ Y) & -(X < Y));  
  
If X < Y, then -(X < Y) = -1, which is all 1’s in two’s complement representation. Therefore, we have Y ^ (X ^ Y) = X.  
If X = Y, then -(X < Y) = 0. Therefore, we have Y ^ 0 = Y.  
  
Performance
*  If and if else statement is used, a miss-predicted branch empties the processor pipeline.
  
---
  
###__Round up to a Power of 2__  
   --iNumber;  
   iNumber |= iNumber >> 1;  
   iNumber |= iNumber >> 2;  
   iNumber |= iNumber >> 4;  
   iNumber |= iNumber >> 8;  
   iNumber |= iNumber >> 16;  
   ++iNumber;  

The decrement and increment is to handle the boundary case when iNumber is a power of 2.
  
---
  
###__Find the least-significant bit__  
Answer = X & (-X);  
Example  

| Variable | Value            |
| -------- |:----------------:|
| X        | 0010000001010000 |
| -X       | 1101111110110000 |
| X & (-X) | 0000000000010000 |
  
---
  
###__Count the number of set (1s) bits in a Byte(s)__  
```
int iCount = 0;  
while(iNumber != 0)  
{  
  iNumber &= iNumber - 1;  
  ++iCount;  
}  
```
Example of a single iteration  

| Variable    | Value            |
| ----------- |:----------------:|
| X           | 0010110111010000 |
| X - 1       | 0010110111001111 |
| X & (X - 1) | 0010110111000000 |  
  
---
  
