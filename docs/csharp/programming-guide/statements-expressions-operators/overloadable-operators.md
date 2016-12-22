---
title: "Operadores sobrecarreg&#225;veis (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Linguagem C#, sobrecarga de operador"
  - "sobrecarga de Operador [C#]"
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operadores sobrecarreg&#225;veis (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# permite tipos definidos pelo usuário sobrecarregar operadores com a definição de funções de membro estático usando o [operador](../../../csharp/language-reference/keywords/operator.md) palavra\-chave.  Nem todos os operadores podem ser sobrecarregados, no entanto, e outros têm restrições, conforme listado nesta tabela:  
  
|Operadores|Overloadability|  
|----------------|---------------------|  
|[\+](../../../csharp/language-reference/operators/addition-operator.md), [\-](../../../csharp/language-reference/operators/subtraction-operator.md), [\!](../../../csharp/language-reference/operators/logical-negation-operator.md), [~](../../../csharp/language-reference/operators/bitwise-complement-operator.md), [\+\+](../../../csharp/language-reference/operators/increment-operator.md), [\-\-](../../../csharp/language-reference/operators/decrement-operator.md), [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md)|Esses operadores unários podem ser sobrecarregados.|  
|[\+](../../../csharp/language-reference/operators/addition-operator.md), [\-](../../../csharp/language-reference/operators/subtraction-operator.md), [\*](../../../csharp/language-reference/operators/multiplication-operator.md), [\/](../../../csharp/language-reference/operators/division-operator.md), [%](../../../csharp/language-reference/operators/modulus-operator.md), [&](../../../visual-basic/language-reference/operators/and-operator.md),                               [&#124;](../../../csharp/language-reference/operators/or-operator.md) , [^](../../../visual-basic/language-reference/operators/xor-operator.md), [\<\<](../../../csharp/language-reference/operators/left-shift-operator.md), [\>\>](../Topic/%3E%3E%20Operator%20\(C%23%20Reference\).md)|Esses operadores binários podem ser sobrecarregados.|  
|[\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md), [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md), [\<](../Topic/%3C%20Operator%20\(C%23%20Reference\).md), [\>](../../../csharp/language-reference/operators/greater-than-operator.md), [\<\=](../../../csharp/language-reference/operators/less-than-equal-operator.md), [\>\=](../Topic/%3E=%20Operator%20\(C%23%20Reference\).md)|Os operadores de comparação podem ser sobrecarregados \(mas consulte a observação após esta tabela\).|  
|[&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)|Os operadores lógicos condicionais não podem ser sobrecarregados, mas eles são avaliados usando `&` e                               `&#124;` , que podem ser sobrecarregados.|  
|[&#91;&#93;](../../../csharp/language-reference/operators/index-operator.md)|O operador de indexação de matriz não pode ser sobrecarregado, mas você pode definir os indexadores.|  
|[\(T\) x](../../../csharp/language-reference/operators/invocation-operator.md)|O operador cast não pode ser sobrecarregado, mas você pode definir novos operadores de conversão \(consulte [explícita](../../../csharp/language-reference/keywords/explicit.md) e [implícita](../../../csharp/language-reference/keywords/implicit.md)\).|  
|[\+\=](../../../csharp/language-reference/operators/addition-assignment-operator.md), [\-\=](../../../csharp/language-reference/operators/subtraction-assignment-operator-1.md), [\*\=](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md), [\/\=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [%\=](../../../csharp/language-reference/operators/modulus-assignment-operator.md), [&\=](../../../csharp/language-reference/operators/and-assignment-operator.md), [&#124;\=](../../../csharp/language-reference/operators/or-assignment-operator.md), [^\=](../../../csharp/language-reference/operators/xor-assignment-operator.md), [\<\<\=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md), [\>\>\=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|Operadores de atribuição não podem ser sobrecarregados, mas `+=`, por exemplo, é avaliada usando `+`, que podem ser sobrecarregados.|  
|[\=](../../../csharp/language-reference/operators/assignment-operator.md), [.](../../../csharp/language-reference/operators/member-access-operator.md), [?:](../../../csharp/language-reference/operators/conditional-operator.md), [??](../../../csharp/language-reference/operators/null-conditional-operator.md), [\-\>](../../../csharp/language-reference/operators/dereference-operator.md), [\=\>](../../../csharp/language-reference/operators/lambda-operator.md), [f\(x\)](../../../csharp/language-reference/operators/invocation-operator.md), [as](../../../csharp/language-reference/keywords/as.md), [checked](../../../csharp/language-reference/keywords/checked.md), [unchecked](../../../csharp/language-reference/keywords/unchecked.md), [default](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md), [delegate](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), [is](../../../csharp/language-reference/keywords/is.md), [new](../../../csharp/language-reference/keywords/new.md), [sizeof](../../../csharp/language-reference/keywords/sizeof.md), [typeof](../../../csharp/language-reference/keywords/typeof.md)|Esses operadores não podem ser sobrecarregados.|  
  
> [!NOTE]
>  Os operadores de comparação se sobrecarregado, devem ser sobrecarregados em pares; ou seja, se `==` está sobrecarregado, `!=` também deve ser sobrecarregados.  O inverso também é verdadeiro e semelhantes para `<` e `>`, e `<=` e `>=`.  
  
 Para sobrecarregar um operador em uma classe personalizada requer a criação de um método na classe com a assinatura correta.  O método deve ser chamado "operador X" onde X é o nome ou símbolo do operador de sobrecarga.  Operadores unários têm um parâmetro e operadores binários possuem dois parâmetros.  Em cada caso, um parâmetro deve ser do mesmo tipo que a classe ou estrutura que declara o operador.  
  
```c#  
public static Complex operator +(Complex c1, Complex c2)  
    {  
        Return new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);  
    }  
  
```  
  
 É comum ter definições que simplesmente retornam imediatamente com o resultado de uma expressão.  Existe um atalho de sintaxe usando `=>` para essas situações.  
  
```c#  
public static Complex operator +(Complex c1, Complex c2) =>  
        new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);  
  
    // Override ToString() to display a complex number   
    // in the traditional format:  
    public override string ToString() => $"{this.real} + {this.imaginary}";  
  
```  
  
 Para obter mais informações, consulte [Como usar sobrecarga de operador para criar uma classe de número complexo](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Instruções, expressões e operadores](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)   
 [por que são operadores sobrecarregados sempre estáticos em c\#?](http://go.microsoft.com/fwlink/?LinkId=112383)