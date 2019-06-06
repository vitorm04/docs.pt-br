---
title: '- Operador -= – Referência de C#'
ms.custom: seodec18
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 9f43a863de69122e251204668af2ea989fcc993c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300083"
---
# <a name="--and---operators-c-reference"></a>Operadores - e -= (Referência de C#)

O operador `-` é compatível com os tipos numéricos internos e com os tipos [delegados](../keywords/delegate.md).

Para obter informações sobre o operador `-` aritmético, consulte as seções [Operadores de adição e subtração unários](arithmetic-operators.md#unary-plus-and-minus-operators) e [Operador de subtração -](arithmetic-operators.md#subtraction-operator--) do artigo [Operadores aritméticos](arithmetic-operators.md).

## <a name="delegate-removal"></a>Remoção de delegado

Para operandos do mesmo tipo [delegado](../keywords/delegate.md), o operador `-` retorna uma instância de delegado que é calculada da seguinte maneira:

- Se ambos os operandos forem não nulos e a lista de invocação do segundo operando for uma sublista contígua apropriada da lista de invocação do primeiro operando, o resultado da operação será uma nova lista de invocação obtida removendo-se as entradas do segundo operando da lista de invocação do primeiro operando. Se a lista do segundo operando corresponder a várias sublistas contíguas na lista do primeiro operando, somente a sublista correspondente mais à direita será removida. Se a remoção resultar em uma lista vazia, o resultado será `null`.
- Se a lista de invocação do segundo operando não for uma sublista contígua apropriada da lista de invocação do primeiro operando, o resultado da operação será o primeiro operando.
- Se o primeiro operando for `null`, o resultado da operação será `null`. Se o segundo operando for `null`, o resultado da operação será o primeiro operando.

A exemplo a seguir mostra como a operação `-` executa a remoção de delegado:

[!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

## <a name="subtraction-assignment-operator--"></a>Operador de atribuição de subtração -=

Uma expressão que usa o operador `-=`, como

```csharp
x -= y
```

equivale a

```csharp
x = x - y
```

exceto que `x` é avaliado apenas uma vez.
  
O exemplo a seguir demonstra o uso do operador `-=`:

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

Você também usará o operador `-=` para especificar um método de manipulador de eventos a remover ao cancelar a assinatura de um [evento](../keywords/event.md). Para obter mais informações, confira [Como assinar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Um tipo definido pelo usuário pode [sobrecarregar](../keywords/operator.md) o operador `-`. Quando um operador `-` binário é sobrecarregado, o operador `-=` também é implicitamente sobrecarregado. Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador `-=`.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja as seções [Operador de subtração unário](~/_csharplang/spec/expressions.md#unary-minus-operator) e [Operador de subtração](~/_csharplang/spec/expressions.md#subtraction-operator) da [Especificação de linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Delegados](../../programming-guide/delegates/index.md)
- [Eventos](../../programming-guide/events/index.md)
- [Checked e unchecked](../keywords/checked-and-unchecked.md)
- [Operadores aritméticos](arithmetic-operators.md)
- [Operadores + e +=](addition-operator.md)
