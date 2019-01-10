---
title: var – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 79a3fe331107a902957158a9631f607cb431be32
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610639"
---
# <a name="var-c-reference"></a>var (Referência de C#)

Começando com o Visual C# 3.0, as variáveis que são declaradas no escopo do método podem ter um “tipo” implícito `var`. Uma variável local de tipo implícito é fortemente tipada, como se você mesmo tivesse declarado o tipo, mas o compilador determina o tipo. As duas declarações a seguir de `i` são funcionalmente equivalentes:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Para obter mais informações, consulte [Variáveis locais de tipo implícito](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) e [Relacionamentos de tipo em operações de consulta LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra duas expressões de consulta. Na primeira expressão, o uso de `var` é permitido, mas não é necessário, pois o tipo do resultado da consulta pode ser declarado explicitamente como um `IEnumerable<string>`. No entanto, na segunda expressão, `var` permite que o resultado seja uma coleção de tipos anônimos e o nome desse tipo não é acessível, exceto para o próprio compilador. O uso de `var` elimina a necessidade de criar uma nova classe para o resultado. Observe que no exemplo 2, a variável de iteração `foreach` `item` também deve ser implicitamente tipada.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Variáveis Locais Tipadas Implicitamente](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)