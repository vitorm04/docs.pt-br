---
title: Tipos não gerenciados – referência em C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 8a4599514115aa21f17c32848ce203fea704072e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846452"
---
# <a name="unmanaged-types-c-reference"></a>Tipos não gerenciados (referência em C#)

Um tipo é um **tipo não gerenciado** se for algum dos seguintes tipos:

- `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`
- Qualquer [tipo de enum](enum.md)
- Qualquer [tipo de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Qualquer tipo de [estrutura](struct.md) definido pelo usuário que contenha apenas campos de tipos não gerenciados e, em C# 7.3 e anterior, não é um tipo construído (um tipo que inclui pelo menos um tipo de argumento)

Começando com C# 7.3, [ `unmanaged` ](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) você pode usar a restrição para especificar que um parâmetro de tipo é um tipo não-ponteiro, não anulado não gerenciado.

Começando com C# 8.0, um tipo de estrutura *construída* que contém campos de tipos não gerenciados também não é gerenciado, como mostra o exemplo a seguir:

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

Uma estrutura genérica pode ser a fonte de ambos os tipos construídos não gerenciados e não não gerenciados. O exemplo anterior define uma `Coords<T>` estrutura genérica e apresenta os exemplos de tipos construídos não gerenciados. O exemplo de não ser `Coords<object>`um tipo não gerenciado é . Não é desgerenciado porque tem os `object` campos do tipo, que não é não gerenciado. Se você quiser que *todos os* tipos construídos `unmanaged` sejam tipos não gerenciados, use a restrição na definição de uma estrutura genérica:

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>especificação da linguagem C#

Para saber mais, confira a seção [Tipos de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-types) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Tipos de Ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos relacionados a memória e extensão](../../../standard/memory-and-spans/index.md)
- [tamanhodo operador](../operators/sizeof.md)
- [Operador stackalloc](../operators/stackalloc.md)
