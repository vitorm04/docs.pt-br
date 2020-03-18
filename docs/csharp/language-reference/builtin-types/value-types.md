---
title: Tipos de valor - referência C#
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 406e5b8bbe0802146a65bb4b9a053e753a7827ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399577"
---
# <a name="value-types-c-reference"></a>Tipos de valor (referência C#)

*Tipos de valor* e [tipos de referência](../keywords/reference-types.md) são as duas principais categorias dos tipos C#. Uma variável de um tipo de valor contém uma instância do tipo. Isso difere de uma variável de um tipo de referência, que contém uma referência a uma instância do tipo. Por padrão, na [atribuição,](../operators/assignment-operator.md)passando um argumento para um método e retornando um resultado do método, os valores variáveis são copiados. No caso de variáveis de tipo de valor, as instâncias de tipo correspondentes são copiadas. O exemplo a seguir demonstra esse comportamento:

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

Como o exemplo anterior mostra, as operações em uma variável de tipo de valor afetam apenas essa instância do tipo de valor, armazenada na variável.

Se um tipo de valor contiver um membro de dados de um tipo de referência, apenas a referência à instância do tipo de referência será copiada quando uma instância de tipo de valor for copiada. Tanto a cópia quanto a instância original do tipo de valor têm acesso à mesma instância do tipo de referência. O exemplo a seguir demonstra esse comportamento:

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Para tornar seu código menos propenso a erros e mais robusto, defina e use tipos de valor imutáveis. Este artigo usa tipos de valor mutáveis apenas para fins de demonstração.

## <a name="kinds-of-value-types"></a>Tipos de tipos de valor

Um tipo de valor pode ser um dos dois tipos a seguir:

- um [tipo de estrutura,](struct.md)que encapsula dados e funcionalidades relacionadas
- um [tipo de enumeração,](enum.md)que é definido por um conjunto de constantes nomeadas e representa uma escolha ou uma combinação de escolhas

Um [tipo](nullable-value-types.md) `T?` de valor anulado representa todos os `T` valores do seu tipo de valor subjacente e um valor [nulo](../keywords/null.md) adicional. Você não `null` pode atribuir a uma variável de um tipo de valor, a menos que seja um tipo de valor anulado.

## <a name="built-in-value-types"></a>Tipos de valor incorporado

C# fornece os seguintes tipos de valor embutidos, também conhecidos como *tipos simples:*

- [Tipos numéricos integrais](integral-numeric-types.md)
- [Tipos numéricos de ponto flutuante](floating-point-numeric-types.md)
- [bool](bool.md) que representa um valor booleano
- [char](char.md) que representa um caractere Unicode UTF-16

Todos os tipos simples são tipos de estrutura e diferem de outros tipos de estrutura, pois permitem certas operações adicionais:

- Você pode usar literais para fornecer um valor de um tipo simples. Por exemplo, `'A'` é um literal do tipo `char` e `2001` é um literal do tipo `int`.

- Você pode declarar constantes dos tipos simples com a palavra-chave [const](../keywords/const.md). Não é possível ter constantes de outros tipos de estrutura.

- Expressões constantes, cujos operands são todas constantes dos tipos simples, são avaliadas no momento da compilação.

Começando com C# 7.0, C# suporta [tuplas de valor](../../tuples.md). Uma tuple de valor é um tipo de valor, mas não um tipo simples.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Tipos de valor](~/_csharplang/spec/types.md#value-types)
- [Tipos simples](~/_csharplang/spec/types.md#simple-types)
- [Variáveis](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Tipos de referência](../keywords/reference-types.md)
