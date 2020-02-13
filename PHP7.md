####PHP7设计与源码实现笔记
1.PHP7的改动 
 - 太空船操作符（用于比较两个表达式 $a 和 $b，如果 $a 小于、等于或大于 $b时，它分别返回-1、0或1。）
 - 标量类型声明，返回值类型声明
 - null合并操作符(新增语法糖??$_GET['is']??1;)
 - define定义常量可以放数组
 - namespace批量导入use com\tutorialspoint\{ClassA, ClassB, ClassC as C};
 - Closure :: call（绑定并调用闭包）
 - Closure :: bind - 使用特定的绑定对象和类范围复制一个闭包
 - throwable接口（错误处理）
 - intdiv（整除）
 - list 赋值(list($a,$b,$c) = [1,2,3])    
 
2.关于增强速度
 - 使用opcache，在之前官方就已经推出了opcache，但是在7中经过广泛的推广大家都推荐开启opche
 - "vld"扩展，php代码在解析过程中通过zend会将.PHP文件编译成opcode，再通过执行解析后得到最终值，通过vld扩展可以有效的知道代码在编译后的结果
 - "dot"描述图形语言，vld通过命令生成dot脚本得到代码执行流程图形