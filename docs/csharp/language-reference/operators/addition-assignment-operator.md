---
title: Operador += (Referência de C#)
ms.date: 10/22/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ee335e3e2e7d352d4e26b802bad2b08a05c666ab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192025"
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

Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de adição](addition-operator.md) `+`, o operador de atribuição de adição`+=` ficará implicitamente sobrecarregado.

Você também usará o operador `+=` para especificar um método de manipulador de eventos ao assinar um [evento](../keywords/event.md). Para obter mais informações, consulte [Como Realizar e Cancelar a Assinatura de Eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

O exemplo a seguir demonstra o uso do operador `+=`:

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Eventos](../../programming-guide/events/index.md)
- [Delegados](../../programming-guide/delegates/index.md)
