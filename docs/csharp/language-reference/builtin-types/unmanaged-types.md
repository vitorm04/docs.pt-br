---
title: Tipos não gerenciados – referência em C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 97aa4dd629e385dbe9641d82a7da21a0aaa63e92
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342588"
---
# <a name="unmanaged-types-c-reference"></a>Tipos não gerenciados (referência em C#)

Um tipo é um **tipo não gerenciado** , se for qualquer um dos seguintes tipos:

- `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`
- Todo tipo [enumerado](enum.md)
- Todo tipo [ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Qualquer tipo de [struct](../keywords/struct.md) definido pelo usuário que contém campos de tipos não gerenciados somente e, C# em 7,3 e anterior, não é um tipo construído (um tipo que inclui pelo menos um argumento de tipo)

A partir C# do 7,3, você pode usar a [restrição`unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) para especificar que um parâmetro de tipo é um tipo não gerenciado não-ponteiro e não anulável.

A partir C# do 8,0, um tipo struct *construído* que contém campos de tipos não gerenciados também é não gerenciado, como mostra o exemplo a seguir:

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

Uma estrutura genérica pode ser a fonte de tipos construídos não gerenciados e não gerenciados. O exemplo anterior define um struct genérico `Coords<T>` e apresenta os exemplos de tipos construídos não gerenciados. O exemplo de um tipo não gerenciado é `Coords<object>`. Não é não gerenciado porque tem os campos do tipo `object`, que não são gerenciados. Se você quiser que *todos os* tipos construídos sejam tipos não gerenciados, use a restrição `unmanaged` na definição de uma struct genérica:

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>especificação da linguagem C#

Para saber mais, confira a seção [Tipos de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-types) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Veja também

- [Referência de C#](../index.md)
- [Tipos de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos relativos a memória e extensão](../../../standard/memory-and-spans/index.md)
- [Operador sizeof](../operators/sizeof.md)
- [Operador stackalloc](../operators/stackalloc.md)
