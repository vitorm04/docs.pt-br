---
title: Tipos que permitem valor nulo – Guia de Programação em C#
ms.custom: seodec18
description: Saiba mais sobre os tipos que permitem valor nulo C# e como usá-los
ms.date: 07/30/2018
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: cd5ac40ca73f7c528a903d5863f3cf5880738f11
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245113"
---
# <a name="nullable-types-c-programming-guide"></a>Tipos que permitem valor nulo (Guia de Programação em C#)

Os tipos que permitem valor nulo são instâncias do struct <xref:System.Nullable%601?displayProperty=nameWithType>. Os tipos que permitem valor nulo podem representar todos os valores de um tipo subjacente `T` e um valor [null](../../language-reference/keywords/null.md) adicional. O tipo subjacente `T` pode ser qualquer [tipo de valor](../../language-reference/keywords/value-types.md) que não permite valor nulo. `T` não pode ser um tipo de referência.

Por exemplo, é possível atribuir `null` ou qualquer valor inteiro de <xref:System.Int32.MinValue?displayProperty=nameWithType> até <xref:System.Int32.MaxValue?displayProperty=nameWithType> a um `Nullable<int>` e [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md) ou `null` a um `Nullable<bool>`.

Use um tipo que permite valor nulo quando precisar representar o valor indefinido de um tipo subjacente. Uma variável booliana pode ter apenas dois valores: true e false. Não há nenhum valor "indefinido". Em muitos aplicativos de programação, principalmente nas interações de banco de dados, um valor de variável pode estar indefinido ou ausente. Por exemplo, um campo em um banco de dados pode conter os valores true ou false ou pode não conter nenhum valor. Use um tipo `Nullable<bool>` nesse caso.

Os tipos que permitem valor nulo têm as seguintes características:
  
- Os tipos que permitem valor nulo representam variáveis de tipo de valor que podem ser atribuídas ao valor `null`. Você não pode criar um tipo que permite valor nulo com base em um tipo de referência. (Os tipos de referência já dão suporte ao valor `null`.)  
  
- A sintaxe `T?` é uma abreviação para `Nullable<T>`. As duas formas são intercambiáveis.  
  
- Atribua um valor a um tipo que permite valor nulo como você faria para um tipo de valor subjacente: `int? x = 10;` ou `double? d = 4.108;`. Também é possível atribuir o valor `null`: `int? x = null;`.  
  
- Use as propriedades somente leitura <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> e <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> para testar em relação ao valor nulo e recuperar o valor, conforme mostrado no exemplo a seguir: `if (x.HasValue) y = x.Value;`  
  
  - A propriedade <xref:System.Nullable%601.HasValue%2A> retornará `true` se a variável contiver um valor ou `false` se for `null`.
  
  - A propriedade <xref:System.Nullable%601.Value%2A> retornará um valor se <xref:System.Nullable%601.HasValue%2A> retornar `true`. Caso contrário, um <xref:System.InvalidOperationException> será gerado.  
  
- Também é possível usar os operadores `==` e `!=` com um tipo que permite valor nulo, conforme mostrado no exemplo a seguir: `if (x != null) y = x.Value;`. Se `a` e `b` forem ambos nulos, `a == b` será avaliado como `true`.  

- A partir do C# 7.0, você pode usar [correspondência de padrões](../../pattern-matching.md#the-is-type-pattern-expression) para examinar e obter um valor de um tipo que permite valor nulo: `if (x is int valueOfX) y = valueOfX;`.
  
- O valor padrão de `T?` é uma instância cuja propriedade <xref:System.Nullable%601.HasValue%2A> retorna `false`.  

- Use o método <xref:System.Nullable%601.GetValueOrDefault> para retornar o valor atribuído ou o valor [padrão](../../language-reference/keywords/default-values-table.md) do tipo de valor subjacente se o valor do tipo que permite valor nulo for `null`.  

- Use o método <xref:System.Nullable%601.GetValueOrDefault(%600)> para retornar o valor atribuído ou o valor padrão fornecido se o valor do tipo que permite valor nulo for `null`.
  
- Use o [operador de coalescência nula](../../language-reference/operators/null-coalescing-operator.md), `??`, para atribuir um valor a um tipo subjacente baseado em um valor do tipo que permite valor nulo: `int? x = null; int y = x ?? -1;`. No exemplo, como `x` é null, o valor de resultado `y` é `-1`.

- Se uma conversão definida pelo usuário for definida entre dois tipos de dados, a mesma conversão também poderá ser usada com as versões que permitem valor nulo desses tipos de dados.
  
- Os tipos que permitem valor nulo aninhados não são permitidos. A linha a seguir não é compilada: `Nullable<Nullable<int>> n;`  

Confira mais informações nos tópicos [Uso de tipos que permitem valor nulo](using-nullable-types.md) e [Como: identificar um tipo que permite valor nulo](how-to-identify-a-nullable-type.md).
  
## <a name="see-also"></a>Consulte também

- <xref:System.Nullable%601?displayProperty=nameWithType>  
- <xref:System.Nullable?displayProperty=nameWithType>  
- [Operador ??](../../language-reference/operators/null-coalescing-operator.md)  
- [Guia de Programação em C#](../index.md)  
- [Guia do C#](../../index.md)  
- [Referência de C#](../../language-reference/index.md)  
- [Tipos de valor que permitem valor nulo (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
