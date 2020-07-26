DataLab 笔记

更加理解位运算的作用
借鉴了部分资料

function 1:
int bitXor(int x, int y);
task: 实现异或操作
x ⊕ y = (¬x ∧ y) ∨ (x ∧¬y)
利用布尔运算：
x ⊕ y = ¬(¬(a ∧ ¬b)) ∧ (¬(¬a ∧ b))

function 2:
int tmin(void);
task: 位运算获得最小补码
min: 0x1000..000
符号位为1, 其余位为0

function 3:
int isTmax(int x);
task: 位运算判断是否为最大补码
max: 0x0111..11
排除情况：-1的补码 和 0xFFFFFFFF

function 4:
int allOddBits(int x);
task: 判断所有奇数位是否均为1
构造掩码
0xAAAAAAAA = 1010 1010 1010 1010 1010 1010 1010 1010

function 5:
int negate(int x);
task: 求-x
各位取反, 末尾加1

function 6:
int isAsciiDigit(int x);
task: 判断是否为数字0 - 9
ASCII: 0 - 9 0x30 - 0x39
+ 0x39 -> negative
- 0x30 -> negative

function 7:
int conditional(int x, int y, int z);
task: 位运算实现x ? y : z 
判断x各位数字 
x == 0 -> 0
x != 0 -> 1
补码: 各位取反, 末尾加1

function 8:
int isLessOrEqual(int x, int y);
task: if x <= y  then return 1, else return 0
情况一: 符号相同 判断差值
情况二：符号不用 正数大

function 9:
int logicalNeg(int x);
task: 位运算实现非
利用补码性质

function 10:
int howManyBits(int x);
task: 补码位数
情况一: 正数 最高位1 + 1
情况二：负数 最高位0 + 1

function 11；
unsigned floatScale2(unsigned uf);
task: 2*f
考虑特殊情况：
0, 正负无穷, NaN
非规格化小数或0时，处理小数部分
NaN或INF时-> uf

function 12:
int floatFloat2Int(unsigned uf);
task: 浮点数转换为整数
如果原浮点值为0 -> 0
如果真实指数大于31 -> 0x80000000u；
如果exponent < 0 -> 0。
剩下的情况：首先把小数部分（23位）转化为整数（和23比较），然后判断是否溢出：如果和原符号相同则直接返回，否则如果结果为负（原来为正）则溢出返回越界指定值0x80000000u，否则原来为负，结果为正，则需要返回其补码（相反数）

function 13:
unsigned floatPower2(int x);
task: 2.0^x
暂时未写出 报错


