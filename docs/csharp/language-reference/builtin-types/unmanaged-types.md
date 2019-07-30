---
title: Tipos não gerenciados – referência em C#
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 2b675be5dbc61006725549f4b69284326650401d
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512069"
---
# <a name="unmanaged-types-c-reference"></a>Tipos não gerenciados (referência em C#)

Um **tipo não gerenciado** é todo tipo que não seja tipo de referência ou tipo construído (tipo que inclui pelo menos um argumento de tipo) e não contenha campos de tipo de referência ou tipo construído em qualquer nível de aninhamento. Em outras palavras, um tipo não gerenciado é um dos seguintes:

- `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`
- Todo tipo [enumerado](../keywords/enum.md)
- Todo tipo [ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Todo tipo [struct](../keywords/struct.md) definido pelo usuário que não seja tipo construído e contenha somente campos de tipos não gerenciados

Começando com o C# 7.3, você pode usar a restrição [`unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) para especificar que um parâmetro de tipo é um tipo não gerenciado diferente de ponteiro.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira a seção [Tipos de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-types) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Tipos de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos relativos a memória e extensão](../../../standard/memory-and-spans/index.md)
- [Operador sizeof](../operators/sizeof.md)
- [Operador stackalloc](../operators/stackalloc.md)
