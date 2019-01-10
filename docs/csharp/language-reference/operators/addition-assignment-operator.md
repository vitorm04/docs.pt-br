---
title: Operador += – Referência de C#
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: 5d48f2fe53a9bb6f781f8d35f1e0983bcaa30f88
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240925"
---
# <a name="-operator-c-reference"></a>Operador += (Referência de C#)

Operador de atribuição de adição.

Uma expressão que usa o operador `+=`, como

```csharp
x += y
```

equivale a

```csharp
x = x + y
```

exceto que `x` é avaliado apenas uma vez.
  
Para tipos numéricos, o [operador de adição](addition-operator.md) `+` calcula a soma dos operandos. Se um ou ambos os operandos for do tipo [cadeia de caracteres](../keywords/string.md), ele concatenará as representações de cadeia de caracteres de seus operandos. Para tipos de delegado, o operador `+` retorna uma nova instância de delegado que é a combinação de seus operandos.

Você também usará o operador `+=` para especificar um método de manipulador de eventos ao assinar um [evento](../keywords/event.md). Confira mais informações em [Como: realizar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

O exemplo a seguir demonstra o uso do operador `+=`:

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de adição](addition-operator.md) `+`, o operador de atribuição de adição`+=` ficará implicitamente sobrecarregado. Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição de adição.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja as seções [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) e [Atribuição de eventos](~/_csharplang/spec/expressions.md#event-assignment) na [Especificação da linguagem C#](../language-specification/index.md).
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Eventos](../../programming-guide/events/index.md)
- [Delegados](../../programming-guide/delegates/index.md)
