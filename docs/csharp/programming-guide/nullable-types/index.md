---
title: Tipos de valor Anulável C# -guia de programação
ms.custom: seodec18
description: Saiba mais C# sobre os tipos de valor anulável e como usá-los
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#]
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: b8b52e7fb34adf65d5c76d59811ea6dd0ab16a98
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396223"
---
# <a name="nullable-value-types-c-programming-guide"></a>Tipos de valores anuláveis (guia deC# programação)

Os tipos de valor anuláveis são instâncias da estrutura <xref:System.Nullable%601?displayProperty=nameWithType>. Tipos de valor anulável podem representar todos os valores de um tipo subjacente `T` e um valor [nulo](../../language-reference/keywords/null.md) adicional. O tipo subjacente `T` pode ser qualquer [tipo de valor](../../language-reference/keywords/value-types.md) que não permite valor nulo. `T` não pode ser um tipo de referência.

> [!NOTE]
> C#8,0 apresenta o recurso de tipos de referência anulável. Para obter mais informações, consulte [tipos de referência anuláveis](../../nullable-references.md). Os tipos de valor anulável estão disponíveis a C# partir de 2.

Por exemplo, é possível atribuir `null` ou qualquer valor inteiro de <xref:System.Int32.MinValue?displayProperty=nameWithType> até <xref:System.Int32.MaxValue?displayProperty=nameWithType> a um `Nullable<int>` e [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md) ou `null` a um `Nullable<bool>`.

Você usa um tipo de valor anulável quando precisa representar o valor indefinido de um tipo subjacente. Uma variável booleana pode ter apenas dois valores: `true` e `false`. Não há nenhum valor "indefinido". Em muitos aplicativos de programação, principalmente nas interações de banco de dados, um valor de variável pode estar indefinido ou ausente. Por exemplo, um campo em um banco de dados pode conter os valores true ou false ou pode não conter nenhum valor. Use um tipo `Nullable<bool>` nesse caso.

Os tipos de valores anuláveis têm as seguintes características:

- Os tipos de valor anuláveis representam variáveis de tipo de valor que podem ser atribuídas ao valor `null`.

- A sintaxe `T?` é uma abreviação para `Nullable<T>`. As duas formas são intercambiáveis.

- Atribua um valor a um tipo de valor anulável exatamente como você faria para um tipo de valor subjacente: `int? x = 10;` ou `double? d = 4.108;`. Também é possível atribuir o valor `null`: `int? x = null;`.

- Use as propriedades somente leitura <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> e <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> para testar em relação ao valor nulo e recuperar o valor, conforme mostrado no exemplo a seguir: `if (x.HasValue) y = x.Value;`

  - A propriedade <xref:System.Nullable%601.HasValue%2A> retornará `true` se a variável contiver um valor ou `false` se for `null`.

  - A propriedade <xref:System.Nullable%601.Value%2A> retornará um valor se <xref:System.Nullable%601.HasValue%2A> retornar `true`. Caso contrário, um <xref:System.InvalidOperationException> será gerado.

- Você também pode usar os operadores `==` e `!=` com um tipo de valor anulável, conforme mostrado no exemplo a seguir: `if (x != null) y = x.Value;`. Se `a` e `b` forem ambos nulos, `a == b` será avaliado como `true`.

- A partir do C# 7.0, você pode usar [correspondência de padrões](../../pattern-matching.md#the-is-type-pattern-expression) para examinar e obter um valor de um tipo que permite valor nulo: `if (x is int valueOfX) y = valueOfX;`.

- O valor padrão de `T?` é uma instância cuja propriedade <xref:System.Nullable%601.HasValue%2A> retorna `false`.

- Use o método <xref:System.Nullable%601.GetValueOrDefault> para retornar o valor atribuído ou o valor [padrão](../../language-reference/keywords/default-values-table.md) do tipo de valor subjacente se o valor do tipo que permite valor nulo for `null`.

- Use o método <xref:System.Nullable%601.GetValueOrDefault(%600)> para retornar o valor atribuído ou o valor padrão fornecido se o valor do tipo que permite valor nulo for `null`.

- Use o [operador de União nulo](../../language-reference/operators/null-coalescing-operator.md), `??`, para atribuir um valor a uma variável de um tipo de valor subjacente com base em um valor de tipo anulável: `int? x = null; int y = x ?? -1;`. No exemplo, como `x` é `null`, o valor de resultado de `y` é `-1`.

- Se uma conversão definida pelo usuário for definida entre dois tipos de valor, a mesma conversão também poderá ser usada com os tipos anuláveis correspondentes.

- Tipos de valores anuláveis aninhados não são permitidos. A linha a seguir não é compilada: `Nullable<Nullable<int>> n;`

Para obter mais informações, consulte os tópicos [usando tipos de valor anulável](using-nullable-types.md) e [como identificar um tipo de valor anulável](how-to-identify-a-nullable-type.md) .

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Operador ??](../../language-reference/operators/null-coalescing-operator.md)
- [Tipos de valor que permitem valor nulo (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
