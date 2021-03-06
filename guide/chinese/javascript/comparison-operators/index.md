---
title: Comparison Operators
localeTitle: 比较运算符
---
JavaScript具有**严格**和**类型转换**比较。

*   严格比较（例如===）仅在操作数类型相同时才为真。
    
*   更常用的抽象比较（例如==）在进行比较之前将操作数转换为相同的Type。
    
*   对于关系抽象比较（例如，<=），操作数首先在比较之前转换为基元，然后转换为相同类型。
    
*   使用Unicode值基于标准词典排序比较字符串。
    

## 比较特点：

*   当两个字符串在相应位置具有相同的字符序列，相同的长度和相同的字符时，它们严格相等。
    
*   当两个数字在数值上相等（具有相同的数值）时，两个数字严格相等。 NaN不等于任何东西，包括NaN。正负零彼此相等。
    
*   如果两个布尔操作数都为真或两者都为假，则它们严格相等。
    
*   对于严格或抽象的比较，两个不同的对象永远不会相等。
    
*   仅当操作数引用相同的Object时，才会使用比较Objects的表达式。
    
*   空和未定义类型严格等于它们自己并且抽象地彼此相等。
    

## 平等运营商

### 平等（==）

如果操作数**不是同一类型** ，则等于运算符会转换操作数，然后应用严格比较。如果**两个操作数都是对象** ，则JavaScript比较内部引用，当操作数引用内存中的同一对象时，这些内部引用相等。

#### 句法
```
 x == y 
```

#### 例子
```
 1   ==  1        // true 
 "1"  ==  1        // true 
 1   == '1'       // true 
 0   == false     // true 
 0   == null      // false 
 
   0   == undefined   // false 
 null  == undefined   // true 
```

### 不平等（！=）

如果操作数不相等，则不等运算符返回true。如果两个操作数**的类型不同** ，则JavaScript会尝试将操作数转换为适当的类型以进行比较。如果**两个操作数都是对象** ，则JavaScript比较内部引用，当操作数引用内存中的不同对象时，这些引用不相等。

#### 句法
```
x != y 
```

#### 例子
```
1 !=   2     // true 
 1 !=  "1"    // false 
 1 !=  '1'    // false 
 1 !=  true   // false 
 0 !=  false  // false 
```

### 身份/严格平等（===）

如果操作数严格相等**而没有类型转换，**则identity运算符返回true。

#### 句法
```
x === y 
```

#### 例子
```
3 === 3   // true 
 3 === '3' // false 
```

### 非身份/严格不平等（！==）

如果操作数**不相等和/或不是相同类型，则**非标识运算符返回true。

#### 句法
```
x !== y 
```

#### 例子
```
3 !== '3' // true 
 4 !== 3   // true 
```

## 关系运算符

### 大于运算符（>）

如果左操作数大于右操作数，则大于运算符返回true。

#### 句法
```
x > y 
```

#### 例子
```
4 > 3 // true 
```

### 运算符大于等于（> =）

如果左操作数大于或等于右操作数，则大于或等于运算符返回true。

#### 句法
```
x >= y 
```

#### 例子
```
4 >= 3 // true 
 3 >= 3 // true 
```

### 小于运算符（<）

如果左操作数小于右操作数，则小于运算符返回true。

#### 句法
```
x < y 
```

#### 例子
```
3 < 4 // true 
```

### 小于等于运算符（<=）

如果左操作数小于或等于右操作数，则小于或等于运算符返回true。

#### 句法
```
x <= y 
```

#### 例子
```
3 <= 4 // true 
```

_您可以在[MDN上](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)找到更多信息。_

## 比较null和undefined

当我们比较null和undefined时，我们会看到不同的行为。让我们通过示例检查不同的场景

#### 示例 - 严格相等检查（===）

console.log（null === undefined）; // O / P - 假

Otuput是假的，这是正确的，因为我们知道“null”和“undefined”是不同的类型。

#### 示例 - 非严格相等性检查（==）

console.log（null == undefined）; // O / P： - 是的

怎么样？这是因为“null”和“undefined”有一个特殊规则。由于它们在非严格检查（==）的情况下是相同的，但不等于任何其他值。

如果我们使用比较运算符，如<，>，<=，> =等，则“null”和“undefined”将转换为数字，在这种情况下，“null”将变为0，“undefined”将为NaN。让我们检查一下这些例子。

#### 示例 - 将null与0（零）进行比较

console.log（null> 0）; // O / P - 假 console.log（null> = 0）; // O / P - 是的 console.log（null == 0）; // O / P - 假

奇怪？根据第一个语句，null不大于0，并且从第二个语句中，null大于或等于0.因此，如果我们以数学方式思考并比较两个语句，则会得到null等于0的结果。 ，按照第三种说法，这不是真的。为什么？

原因是“比较”和“平等检查”都以不同的方式起作用。 相比之下，“null / undefined”首先转换为数字，因此，在前两种情况下，“null”变为0，因此case1）（null> 0） - > false和case2）（null> = 0） - > true。 但是，在等式检查（==）中，“null / undefined”在没有任何转换的情况下工作，并且如上所述（特殊规则），在等式检查中，“null / undefined”仅相互等于并且不等于其他任何内容。因此（null == 0） - > false。

#### 示例 - 将undefined与0（零）进行比较

console.log（undefined> 0）; // O / P - 假 console.log（undefined> = 0）; // O / P - 假 console.log（undefined == 0）; // O / P - 假

在这里，我们测试与null相同的情况，但结果又不同。为什么？

原因如下。 在前两种情况下，我们将undefined与0进行比较，并且如上所述，比较undefined会转换为NaN。 NaN是一个特殊值，与任何数字相比总是返回false，这就是我们在前两种情况下输出为false的原因。 对于第三个陈述，原因与“null”中提到的相同。在等式检查中，“null / undefined”仅相互等于并且不等于其他任何内容。因此（undefined == 0） - > false。