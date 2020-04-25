# week03 总结

## 语法

### 表达式

运算符的优先级

1. member 属性表达

- a.b
- a[b]
- foo`string`
- super.b
- super['b']

2. New

- new Foo()

call

- foo()
- super()
- foo()['b']
- foo().b

### 语句

#### Grammar

- 简单语句
  ExpressionStatement => a + b = 1
  EmptyStatement => ;
  DebuggerStatement => debugger;
  ThrowStatement => throw a;
  ContinueStatement => continue label1;
  BreakStatement => break label2;
  ReturnStatement => return a == 2;
- 复合语句
  BlockStatement
  IterationStatement for 本身会产生一个作用域，范围在 block 之外
  IfStatement
  SwitchStatement

* 声明
  FuntionDeclaration
  GeneratorDeclaration
  AsyncFunctionDeclaration
  AsyncGeneratorDeclaration
  VariableStatement (包含以上四种声明)
  ClassDeclaration
  LexicalDeclaration

#### Runtime

- Completion Record
  - [[type]]: normal , break, continue, return or throw
  - [[value]]: Types
  - [[target]]: label
- Lexical Environment
