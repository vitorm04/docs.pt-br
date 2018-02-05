---
title: "Operadores sobrecarregáveis (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7487f398ec412c4a302054ade20800f431e2c793
ms.sourcegitcommit: 22a48b64a0150a60b00b4fc4d8c62cde7f1670c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="overloadable-operators-c-programming-guide"></a>Operadores sobrecarregáveis (Guia de Programação em C#)

O C# permite que tipos definidos pelo usuário sobrecarreguem operadores definindo funções de membro estático usando a palavra-chave [operator](../../../csharp/language-reference/keywords/operator.md). No entanto, nem todos os operadores podem ser sobrecarregados e outros têm restrições, conforme listado nesta tabela:

| Operadores | Capacidade de sobrecarga |
| --------- | --------------- |
|[+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [!](../../../csharp/language-reference/operators/logical-negation-operator.md), [~](../../../csharp/language-reference/operators/bitwise-complement-operator.md), [++](../../../csharp/language-reference/operators/increment-operator.md), [--](../../../csharp/language-reference/operators/decrement-operator.md), [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md)|Esses operadores unários podem ser sobrecarregados.|
|[+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [\*](../../../csharp/language-reference/operators/multiplication-operator.md), [/](../../../csharp/language-reference/operators/division-operator.md), [%](../../../csharp/language-reference/operators/modulus-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md), [^](../../../csharp/language-reference/operators/xor-operator.md), [\<\<](../../../csharp/language-reference/operators/left-shift-operator.md), [>>](../../../csharp/language-reference/operators/right-shift-operator.md)|Esses operadores binários podem ser sobrecarregados.|
|[==](../../../csharp/language-reference/operators/equality-comparison-operator.md), [!=](../../../csharp/language-reference/operators/not-equal-operator.md), [\<](../../../csharp/language-reference/operators/less-than-operator.md), [>](../../../csharp/language-reference/operators/greater-than-operator.md), [\<=](../../../csharp/language-reference/operators/less-than-equal-operator.md), [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md)|Operadores de comparação podem ser sobrecarregados (consulte a observação após esta tabela).|
|[&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)|Os operadores lógicos condicionais não podem ser sobrecarregados, mas são avaliados usando `&` e <code>&#124;</code>, que podem ser sobrecarregados.|
|[&#91;&#93;](../../../csharp/language-reference/operators/index-operator.md)|O operador de indexação de matriz não pode ser sobrecarregado, mas você pode definir indexadores.|
|[(T)x](../../../csharp/language-reference/operators/invocation-operator.md)|O operador de conversão não pode ser sobrecarregado, mas você pode definir novos operadores de conversão (consulte [explicit](../../../csharp/language-reference/keywords/explicit.md) e [implicit](../../../csharp/language-reference/keywords/implicit.md)).|
|[+=](../../../csharp/language-reference/operators/addition-assignment-operator.md), [-=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [\*=](../../../csharp/language-reference/operators/multiplication-assignment-operator.md), [/=](../../../csharp/language-reference/operators/division-assignment-operator.md), [%=](../../../csharp/language-reference/operators/modulus-assignment-operator.md), [&=](../../../csharp/language-reference/operators/and-assignment-operator.md), [&#124;=](../../../csharp/language-reference/operators/or-assignment-operator.md), [^=](../../../csharp/language-reference/operators/xor-assignment-operator.md), [\<\<=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md), [>>=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|Operadores de atribuição não podem ser sobrecarregados, mas `+=`, por exemplo, é avaliado usando `+`, que pode ser sobrecarregado.|
|[=](../../../csharp/language-reference/operators/assignment-operator.md), [.](../../../csharp/language-reference/operators/member-access-operator.md), [?:](../../../csharp/language-reference/operators/conditional-operator.md), [??](../../../csharp/language-reference/operators/null-conditional-operator.md), [->](../../../csharp/language-reference/operators/dereference-operator.md), [=>](../../../csharp/language-reference/operators/lambda-operator.md), [f(x)](../../../csharp/language-reference/operators/invocation-operator.md), [as](../../../csharp/language-reference/keywords/as.md), [checked](../../../csharp/language-reference/keywords/checked.md), [unchecked](../../../csharp/language-reference/keywords/unchecked.md), [default](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), [delegate](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), [is](../../../csharp/language-reference/keywords/is.md), [new](../../../csharp/language-reference/keywords/new.md), [sizeof](../../../csharp/language-reference/keywords/sizeof.md), [typeof](../../../csharp/language-reference/keywords/typeof.md)|Esses operadores não podem ser sobrecarregados.|

> [!NOTE]
> Os operadores de comparação, se sobrecarregados, devem ser sobrecarregados em pares. Ou seja, se `==` for sobrecarregado, `!=` também deve ser sobrecarregado. O contrário também é verdadeiro, no qual sobrecarregar `!=` requer uma sobrecarga para `==`. O mesmo vale para os operadores de comparação `<` e `>` e para `<=` e `>=`.

Sobrecarregar um operador em uma classe personalizada requer a criação de um método na classe com a assinatura correta. O método deve ser nomeado "operador X", em que X é o nome ou o símbolo do operador sobrecarregado. Operadores unários têm um parâmetro e operadores binários têm dois parâmetros. Em cada caso, um parâmetro deve ser do mesmo tipo que a classe ou struct que declara o operador.

```csharp
public static Complex operator +(Complex c1, Complex c2)
{
    return new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);
}
```

É comum ter definições que simplesmente retornam imediatamente com o resultado de uma expressão.  Há um atalho de sintaxe que usa `=>` para essas situações.

```csharp
public static Complex operator +(Complex c1, Complex c2) =>
        new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);
  
// Override ToString() to display a complex number in the traditional format:
public override string ToString() => $"{this.real} + {this.imaginary}";
```

Para obter mais informações, consulte [Como usar sobrecarga de operador para criar uma classe de número complexo](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md).

## <a name="see-also"></a>Consulte também

[Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
[Instruções, expressões e operadores](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
[Operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
[Operadores do C#](../../../csharp/language-reference/operators/index.md)  
[Por que os operadores sobrecarregados sempre são estáticos em C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
