# SCPU
## RISC-V 架构
1. ISA Classes(类别)
   - 栈结构(stack)
   - 累加器结构(accumulator)
   - 通用目的寄存器结构(General-Purpose Register)
      + Register-Memory Arch：任何指令都可以访问内存
      + Load-Store Architecture：只有load和store可以访问内存
      + Memory-memory Architecture：效率太低
2. 不同结构的代码长度不同，例如D = A*B-(A+C*B)
   - stack:
    ```
    push A
    push B
    mul
    push A
    push C
    push B
    mul
    add
    sub
    pop D
    ```
   - accumulator
     ```
     load A
     mul B
     store D
     load C
     mul B
     add A
     store A
     load D
     sub A
     store D
     ```

3. 小端序和大端序：
   - 小端序(little endian)：低地址存低位数据
   - 大端序(big endian)：低地址存高位数据


4. x1作为默认返回地址
   
5. 动态地址：编译时无法确定的地址，需要运行时确定
   静态地址：编译时就可以确定


