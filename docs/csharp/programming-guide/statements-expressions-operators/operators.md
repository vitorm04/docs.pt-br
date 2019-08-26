---
title: Operadores – Guia de Programação em C#
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 4870c744383205c2b7e3832c01fb838a545f085f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588611"
---
# <a name="operators-c-programming-guide"></a>Operadores (Guia de Programação em C#)

Em C#, um *operador* é um elemento de programa aplicado a um ou mais *operandos* em uma expressão ou instrução. Os operadores que usam um operando, como o operador de incremento (`++`) ou `new`, são referidos como operadores *unários*. Os operadores que usam dois operandos, como operadores aritméticos (`+`,`-`,`*`,`/`), são referidos como operadores *binários*. Um operador, o operador condicional (`?:`), usa três operandos e é o único operador ternário em C#.  
  
 A seguinte instrução de C# contém um único operador unário e um operando único. O operador de incremento, `++`, modifica o valor do operando `y`.  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 A seguinte instrução de C# contém dois operadores binários, cada um com dois operandos. O operador de atribuição, `=`, contém a variável inteira `y` e a expressão `2 + 3` como operandos. A expressão `2 + 3` em si consiste no operador de adição e dois operandos, `2` e `3`.  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
Um operando pode ser uma expressão válida composta por qualquer comprimento de código e pode incluir qualquer número de subexpressões. Em uma expressão que contém vários operadores, a ordem em que os operadores são aplicados é determinada pela *precedência de operadores*, *associatividade* e parênteses.  

## <a name="operator-precedence"></a>Precedência do operador
  
Cada operador possui uma precedência definida. Em uma expressão com vários operadores e diferentes níveis de precedência, a precedência dos operadores determina a ordem em que os operadores são avaliados. Por exemplo, a seguinte instrução atribui 3 a `n1`:

```csharp
n1 = 11 - 2 * 4;
```

A multiplicação é executada primeiro porque ela tem precedência sobre a subtração.

Para obter a lista completa de operadores do C# ordenada pelo nível de precedência, confira [Operadores do C#](../../language-reference/operators/index.md).
  
## <a name="associativity"></a>Associatividade

 Quando dois ou mais operadores com a mesma precedência estiverem presentes em uma expressão, eles serão avaliados com base em associatividade. Os operadores associativos esquerdos são avaliados em ordem da esquerda para a direita. Por exemplo, `x * y / z` é avaliado como `(x * y) / z`. Os operadores associativos direitos são avaliados em ordem da direita para a esquerda. Por exemplo, o operador de atribuição é associativo direito. Se ele não fosse, o código a seguir resultaria em um erro.  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 Como outro exemplo, o operador ternário ([?:](../../language-reference/operators/conditional-operator.md)) é associativo à direita. A maioria dos operadores binários são associativos à esquerda.  
  
 Se os operadores em uma expressão forem associativos direitos ou esquerdos, os operandos de cada expressão serão avaliados primeiro, da esquerda para a direita. Os exemplos a seguir ilustram a ordem de avaliação de operadores e operandos.  
  
|Instrução|Ordem de avaliação|  
|---------------|-------------------------|  
|`a = b`|a, b, =|  
|`a = b + c`|a, b, c, +, =|  
|`a = b + c * d`|a, b, c, d, *, +, =|  
|`a = b * c + d`|a, b, c, *, d, +, =|  
|`a = b - c + d`|a, b, c, -, d, +, =|  
|`a += b -= c`|a, b, c, -=, +=|  
  
## <a name="adding-parentheses"></a>Adicionando parênteses

 Você pode alterar a ordem imposta pela precedência de operadores e a associatividade ao usar parênteses. Por exemplo, `2 + 3 * 2` resulta normalmente em 8, pois operadores multiplicativos têm precedência sobre operadores aditivos. No entanto, se você escrever a expressão como `(2 + 3) * 2`, a adição será avaliada antes da multiplicação e o resultado será 10. Os exemplos a seguir ilustram a ordem de avaliação em expressões com parênteses. Como nos exemplos anteriores, os operandos são avaliados antes que o operador seja aplicado.  
  
|Instrução|Ordem de avaliação|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>Sobrecarga de operador

Você pode define o comportamento de determinados operadores para classes e structs personalizados. Esse processo é chamado *sobrecarga de operador*. Para obter mais informações, consulte [Sobrecarga de operador](../../language-reference/operators/operator-overloading.md).
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Instruções, expressões e operadores](index.md)
- [Operadores do C#](../../language-reference/operators/index.md)
