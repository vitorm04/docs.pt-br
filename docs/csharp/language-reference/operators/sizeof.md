---
title: Operador sizeof – referência em C#
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: a9e80ecb3288479a2ca81b43c9d088809ed5f2f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847281"
---
# <a name="sizeof-operator-c-reference"></a>Operador sizeof (referência em C#)

O operador `sizeof` retorna o número de bytes ocupados por uma variável de um determinado tipo. O argumento do operador `sizeof` deve ser o nome de um [tipo não gerenciado](../builtin-types/unmanaged-types.md) ou um parâmetro de tipo que seja [restrito](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) a um tipo não gerenciado.

O operador `sizeof` exige um contexto [não seguro](../keywords/unsafe.md). No entanto, as expressões apresentadas na tabela a seguir são avaliadas em tempo de compilação para os valores constantes correspondentes e não exigem um contexto não seguro:

|Expression|Valor constante|
|---------|---------------|
|`sizeof(sbyte)`|1|
|`sizeof(byte)`|1|
|`sizeof(short)`|2|
|`sizeof(ushort)`|2|
|`sizeof(int)`|4|
|`sizeof(uint)`|4|
|`sizeof(long)`|8|
|`sizeof(ulong)`|8|
|`sizeof(char)`|2|
|`sizeof(float)`|4|
|`sizeof(double)`|8|
|`sizeof(decimal)`|16|
|`sizeof(bool)`|1|

Você também não precisará usar um contexto não seguro quando o operando do operador `sizeof` for o nome de um tipo [enumerado](../builtin-types/enum.md).

O exemplo a seguir demonstra o uso do operador `sizeof`:

[!code-csharp[sizeof examples](snippets/SizeOfOperator.cs)]

O operador `sizeof` retorna o número de bytes que seriam alocados pelo Common Language Runtime na memória gerenciada. Para tipos [struct](../builtin-types/struct.md), esse valor inclui todo o preenchimento, como demonstra o exemplo anterior. O resultado do operador `sizeof` pode ser diferente do resultado do método <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, que retorna o tamanho de um tipo na memória *não gerenciada*.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira a seção [O operador sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator), nas [especificações da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
- [Operadores relacionados a ponteiro](pointer-related-operators.md)
- [Tipos de Ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos relacionados a memória e extensão](../../../standard/memory-and-spans/index.md)
- [Genéricos no .NET](../../../standard/generics/index.md)
