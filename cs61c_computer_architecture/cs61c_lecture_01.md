# CS 61C: Great Ideas in Computer Architecture (LECTURE 1)
These notes are based on the Berkeley CS 61C course on computer architecture.

## The 6 great ideas in computer architecture
- Abstraction
    - Hiding unnecessary details from the layer above so it can do it’s job without getting bogged down in the details of how the layer below works/is implemented.
- Moore’s law
    - Design systems to outlive the trends of today
    - Look ahead, try to plan for what you’ll need rather than what’s taking the world by storm right now
- Principle of locality
    - Programs follow predictable patterns
    - The ways programs run can give insight into how to design computer systems better
    - Memory hierarchy == accessing data that’s closer over further away
- Parallelism
- Performance measurement and continuous improvement
- Dependability through redundancy
- Moore’s Law is named after Gordon Moore, cofounder of Intel
- Moore’s law states that the more processors you can add to a chip, the cheaper they will become by using less material
- Because it takes longer to put the super tiny transistors of today into a chip, Moore’s law is reversing: the more transistors you add, the more expensive the chip is

## Number representation
- With two’s complement, roughly half of all representable numbers are positive, the other half negative, and you have one number reserved for zero
- With two’s complement, you’ll have more negative numbers than positive ones because one of the positive ones is reserved for zero
- Unsigned integers are reserved for memory addresses
- Leftmost bit is the sign bit in two’s complement
- Highest two’s complement number in binary = 0111 1111 … 1111
- Lowest two’s complement number in binary = 1000 0000 … 0000
- To quickly convert two’s complement numbers: invert all the bits, then add 1
- When adding two’s complement numbers, you throw out the overflow bit unless the sum is greater than the highest representable number.

- everything is number
  - stored w fixed size
    - 8 byte 16 half word 32 word 64 double word 
    - bits
- overflow = too large to represent
- underflow = too small to represent
