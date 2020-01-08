---
title: Operador sizeof – referência em C#
ms.custom: seodec18
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 4488e2313a58a24e324001a4dccdee86a456bb5b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345257"
---
# <a name="sizeof-operator-c-reference"></a>Operador sizeof (referência em C#)

O operador `sizeof` retorna o número de bytes ocupados por uma variável de um determinado tipo. O argumento do operador `sizeof` deve ser o nome de um [tipo não gerenciado](../builtin-types/unmanaged-types.md) ou um parâmetro de tipo que seja [restrito](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) a um tipo não gerenciado.

O operador `sizeof` exige um contexto [não seguro](../keywords/unsafe.md). No entanto, as expressões apresentadas na tabela a seguir são avaliadas em tempo de compilação para os valores constantes correspondentes e não exigem um contexto não seguro:

|Expressão|Valor constante|
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

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

O operador `sizeof` retorna o número de bytes que seriam alocados pelo Common Language Runtime na memória gerenciada. Para tipos [struct](../keywords/struct.md), esse valor inclui todo o preenchimento, como demonstra o exemplo anterior. O resultado do operador `sizeof` pode ser diferente do resultado do método <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, que retorna o tamanho de um tipo na memória *não gerenciada*.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira a seção [O operador sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator), nas [especificações da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Veja também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Operadores relacionados a ponteiro](pointer-related-operators.md)
- [Tipos de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos relativos a memória e extensão](../../../standard/memory-and-spans/index.md)
- [Genéricos no .NET](../../../standard/generics/index.md)
