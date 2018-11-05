---
title: Operador %= (Referência de C#)
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: ab3a6a8d5cbfeb4d527ca1f9c233ddfaba3d35ff
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188710"
---
# <a name="-operator-c-reference"></a>Operador %= (Referência de C#)

Operador de atribuição restante.

Uma expressão que usa o operador `%=`, como  

```csharp
x %= y
```  

equivale a  

```csharp
x = x % y
```  

exceto que `x` é avaliado apenas uma vez.
  
O [operador remainder](remainder-operator.md) `%` calcula o restante após a divisão de seus operandos. Ele é compatível com todos os tipos numéricos.

Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de resto](remainder-operator.md) `%`, o operador de atribuição de resto `%=` ficará implicitamente sobrecarregado.
  
O exemplo a seguir demonstra o uso do operador `%=`:

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
