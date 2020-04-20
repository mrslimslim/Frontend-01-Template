# week02 总结

## 编程语言通识

### 语言按语法分类

#### 非形式语言
中文 英文

#### 形式语言(乔姆斯基谱系)
* 0型 无限制文法（相对无限制）
例子:

* 1型 上下文相关文法
例子：

* 2型 上下文无关文法(大部分语言总体上，比如JS)
例子：

* 3型 正则文法
例子：


补充：现代语言 分为 词法和语法


#### 产生式(BNF) 为了学习形式语言，描述语言

* 用尖括号括起来的名称来表示语法的结构名
* 语法结构分为基础结构和需要其他语法结构定义的复合结构
  基础结构称终结符 比如：*
  复合结构成为非终结符 比如： 1 + 1
* 引号和中间的字符表示终结符
* 可以有括号
* *表示重复多次
* |表示或
* +表示至少一次

练习：加深了解
完成语言
终结符 "a"

终结符 "b"

<Program> := "a"+ | "b"+ (+不能有空格)  =》 重复的 a  b

// 递归
<Program> := <Program> "a"+ | <Program> "b"

// 定义数字
<Number> := "0" | ... | "9"

<DecimalNumber> := "0" | ("1" | ... | "9") <Number>* )

// 加法 表达方式
<AddtiveExpression> := <MultiplicativeExpression> | <AddtiveExpression> "+" <MultiplicativeExpression> |
<AddtiveExpression> "-" <MultiplicativeExpression>


##### 产生式(BNF) 
四则运算
* 1 + 2*3
终结符
* Number
  \* \+ \- \* \/
非终结符
MultiplicativeExpression
AddtiveExpression
LogicalExpression

<MultiplicativeExpression> = <DecimalNumber> | <MultiplicativeExpression> '*' <DecimalNumber> |
<MultiplicativeExpression> '/' <DecimalNumber>

<LogicalExpression> = <AddtiveExpression> | <LogicalExpression> '||' <AddtiveExpression> |
<LogicalExpression> '&&' <AddtiveExpression>

<PrimaryExpression> = <DecimalNumber> | "(" <PrimaryExpression> ")"

###  通过产生式理解乔姆斯基谱系

* 0型 无限制文法 规则：<a> <b> ::= "c" 等号两边 可以产生多个非终结符 约束较少
  * ?::=?  
* 1型 上下文相关文法 规则："condi1" <b> "condi2" ::= "condi1" "x" "condi2" 需要前后都在同样条件 js中的例子：{get a {return 1}},get: 1} ; 2 ** 1 ** 2
  * ?<A>?::=?<B> 
* 2型 上下文无关文法 规则：比较常见的一种  <b> = "x"
  * <A>::=?
* 3型 正则文法 规则：只能够左递归 : <A>::=<A> ? <A>只能出现在最左侧
  * <A>::=<A> ?  
  * <A>::=<A> x


### 现代语言的特例
* C++中，* 可能表示乘号或者指针，具体是哪个，取决于星号签的标识符是否被声明为类型
* VB中，<可能是小于号，也可能是XML直接量的开始，取决于当前位置是否可以接受XML直接量
* Python中，行首的tab符合空格会根据上一行的行首空白以一定规则被处理成虚拟终结符indent或者dedent
* Javascript中，/可能是除号，也可能是正则表达式开头，处理方式类似于VB

### 语言的分类

* 形式语言-用途
  * 数据描述语言 JSON,HTML,XAML,SQL,CSS
  * 编程语言 C C++ C# JS Lisp
* 形式语言-表达方式
  * 声明式语言 JSON,HTML,XAML,SQL,CSS,Lisp,Clojure
  * 命令式语言 C C++ C# JS Lisp Python Ruby

### 图灵完备性
  
* 图灵完备性
  * 命令式 —— 图灵机
   * goto 
   * if和while
* 声明式 ——lambda
   * 递归

### 动态语言

* 动态：
  * 在用户的设备/在线服务器上
  * 产品实际运行时
  * Runtime (产品实际运行时间)
* 静态
  * 在程序员设备上
  * 产品开发式
  * Compiletime

### 类型系统

* 动态类型系统和静态类型系统
* 强类型和弱类型 （有隐式类型的就是弱类型）
  * String + Number （隐式类型转换）
  * String == Boolean
* 复合类型
  * 结构体
  * 函数签名 (T1, T2) => T3
* 子类型
  * 逆变/协变 (凡事能用Array<Parent>的地方，都能用Array<Child> => 协变； 凡事能用Function<Child>的地方，都能用Function<Parent>)


### 一般命令式编程语言

* Atom
  * Identifier : const val  (val为Identifier)
  * Literal :const val = {} ({}为Literal)
* Expression
  * Atom
  * Operator (运算符)
  * Punctuator (标点符号)
* Statement
  * Expression
  * Keyword
  * Punctuator
* Structure
  * Function
  * Class
  * Process
  * Namespace
* Program
  * Program
  * Module
  * Package
  * Library


## 深入学习Javascript
Atom
unicode 兼容ASCII (字符集 https://en.wikipedia.org/wiki/Unicode https://www.fileformat.info/info/unicode) 码点 ASCII https://zh.wikipedia.org/wiki/ASCII

建议命名不要超出ASCII的编码合集

注意：

The terminal symbols of this grammar are all composed of characters in the Unicode Basic Multilingual Plane (BMP).

InputElement
  whitespace  // 空格
  LineTerminator // 换行符
  Comment // 注释
  Token // 标记
    结构
    Punctuator(( ) = < > ;)
    Keywords(for break continue)
    
    内容
    IdentifierName (i document write window addEventListener): 变量名(identifierReference 不能和关键词重合) 属性(可以和关键词重合)
    Literal(NumberLiteral StringLiteral Template) (128 'a')


Type
Number

    IEEE 754 Double Float

String

Boolean

Object

Null

Undefined

Symbol
    
    