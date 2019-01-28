---
title: Operador ^ – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 16419342fec9d6c9845e19e434787c5e4f5a5b12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632238"
---
# <a name="-operator-c-reference"></a>Operador ^ (referência do C#)

Os operadores binários `^` são predefinidos para os tipos integrais e `bool`. Para os tipos integrais, o `^` computa o OR exclusivo bit a bit de seus operandos. Para operandos `bool`, o `^` computa o OR exclusivo lógico de seus operandos; ou seja, o resultado será `true` se e somente se exatamente um dos operandos for `true`.

## <a name="remarks"></a>Comentários

Os tipos definidos pelo usuário podem sobrecarregar o operador `^` (consulte [operador](../keywords/operator.md)). As operações em tipos integrais geralmente são permitidas na enumeração.

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#30)]

O cálculo de `0xf8 ^ 0x3f` no exemplo anterior executa um OR exclusivo bit a bit dos dois valores binários a seguir, que correspondem aos valores hexadecimais F8 e 3F:

`1111 1000`

`0011 1111`

O resultado do OR exclusivo é `1100 0111`, que é igual a C7 em hexadecimal.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
