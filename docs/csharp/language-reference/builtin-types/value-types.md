---
title: Tipos de valor C# -referência
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 6b96d65f657f2af1af5c9a245e956640ee06260e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76748513"
---
# <a name="value-types-c-reference"></a>Tipos de valorC# (referência)

*Tipos de valor* e [tipos de referência](../keywords/reference-types.md) são as duas categorias C# principais de tipos. Uma variável de um tipo Value contém uma instância do tipo. Isso é diferente de uma variável de um tipo de referência, que contém uma referência a uma instância do tipo. Por padrão, na [atribuição](../operators/assignment-operator.md), passando um argumento para um método ou retornando um resultado de método, valores de variáveis são copiados. No caso de variáveis de tipo de valor, as instâncias de tipo correspondentes são copiadas. O exemplo a seguir demonstra esse comportamento:

[!code-csharp[copy of values](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ValueTypeCopied)]

Como mostra o exemplo anterior, as operações em uma variável de tipo de valor afetam apenas essa instância do tipo de valor, armazenado na variável.

Se um tipo de valor contiver um membro de dados de um tipo de referência, somente a referência à instância do tipo de referência será copiada quando uma instância de tipo de valor for copiada. A instância de tipo de valor de cópia e original tem acesso à mesma instância de tipo de referência. O exemplo a seguir demonstra esse comportamento:

[!code-csharp[shallow copy](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Para tornar seu código menos propenso a erros e mais robusto, defina e use tipos de valor imutável. Este artigo usa tipos de valores mutáveis somente para fins de demonstração.

## <a name="kinds-of-value-types"></a>Tipos de tipos de valor

Um tipo de valor pode ser um dos dois tipos a seguir:

- um [tipo de estrutura](../keywords/struct.md), que encapsula dados e funcionalidade relacionada
- um [tipo de enumeração](enum.md), que é definido por um conjunto de constantes nomeadas e representa uma opção ou uma combinação de opções

Um [tipo de valor anulável](nullable-value-types.md) `T?` representa todos os valores de seu tipo de valor subjacente `T` e um valor [nulo](../keywords/null.md) adicional. Você não pode atribuir `null` a uma variável de um tipo de valor, a menos que seja um tipo de valor anulável.

## <a name="built-in-value-types"></a>Tipos de valores internos

C#fornece os seguintes tipos de valor internos, também conhecidos como *tipos simples*:

- [Tipos numéricos inteiros](integral-numeric-types.md)
- [Tipos numéricos de ponto flutuante](floating-point-numeric-types.md)
- [bool](bool.md) que representa um valor booliano
- [Char](char.md) que representa um caractere Unicode UTF-16

Todos os tipos simples são tipos de estrutura e diferem de outros tipos de estrutura, pois permitem determinadas operações adicionais:

- Você pode usar literais para fornecer um valor de um tipo simples. Por exemplo, `'A'` é um literal do tipo `char` e `2001` é um literal do tipo `int`.

- Você pode declarar constantes dos tipos simples com a palavra-chave [const](../keywords/const.md). Não é possível ter constantes de outros tipos de estrutura.

- Expressões constantes, cujos operandos são todas constantes dos tipos simples, são avaliadas no momento da compilação.

A partir C# do 7,0 C# , o dá suporte a [tuplas de valor](../../tuples.md). Uma tupla de valor é um tipo de valor, mas não um tipo simples.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Tipos de valor](~/_csharplang/spec/types.md#value-types)
- [Tipos simples](~/_csharplang/spec/types.md#simple-types)
- [Variáveis](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Veja também

- [Referência de C#](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Tipos de referência](../keywords/reference-types.md)
