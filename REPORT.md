Name: Nicholas Castellanos email: ncast094@gmail.com

Overall in this lab I was able to implemt a MIPS control unit to generate the control singlas 
base on the instruction opcode. Control unit was already integrated with ALU controls and modules 
based on my last Lab (2) work.

Finally with testing I used the first testcase to help build the rest of the following testcases
to verify the behavior of the control unit. Here are the following I tested:
- **R-type AND** instruction  
- **R-type OR** instruction  
- **R-type ADD** instruction  
- **R-type SUB** instruction  
- **R-type SLT** instruction  
- **R-type NOR** instruction  
- **ADDI (add immediate)** instruction  
- **LW (load word)** instruction  
- **SW (store word)** instruction  
- **BEQ (branch equal)** instruction  

All these test cases passed successfully.

For both **ADD** and **ADDI** they perform addition, however in what they differ is 
in how operands and destination registers are selected in the datapath, which results in
different control signals.

- **RegDst:**: ADD is set to `RegDst = 1` due to the destination register coming from the
  `rd` field of the instruction. While ADDI is set to `RegDst = 0` due to the destination
  register coming from the `rt` field.
- **ALUSrc:**: ADD is set to `ALUSrc = 0` since both operands are read from the registers.
  While ADDI is set to `ALUSrc = 1` because the second operand comes from the sign-extended
  immediate value.
- **ALUOp:**: ADD is set to `ALUOp = 10` to show an R-type instruction where the ALU operation
  is determined by the function field. While ADDI is set to `ALUOp = 00` because the ALU
  always performs addition and does not depend on the function field.

