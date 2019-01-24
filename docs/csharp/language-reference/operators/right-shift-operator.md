---
title: Operador &gt;&gt; – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 80e38d8e75b9ad573b635d544d6381950f107583
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333675"
---
# <a name="gtgt-operator-c-reference"></a>Operador &gt;&gt; (referência do C#)

O operador de deslocamento para a direita (`>>`) desloca o primeiro operando à direita pelo número de bits especificado pelo seu segundo operando.

## <a name="remarks"></a>Comentários

Se o primeiro operando for um [int](../keywords/int.md) ou [uint](../keywords/uint.md) (quantidade de 32 bits), a contagem de deslocamento será determinada pelos cinco bits de ordem inferior do segundo operando (segundo operando &0x1f).

Se o primeiro operando for um [long](../keywords/long.md) ou [ulong](../keywords/ulong.md) (quantidade de 64 bits), a contagem de deslocamento será determinada pelos seis bits de ordem inferior do segundo operando (segundo operando & 0x3f).

Se o primeiro operando for um [int](../keywords/int.md) ou [long](../keywords/long.md), o deslocamento para a direita será um deslocamento aritmético (bits vazios de ordem superior devem ser definidos como o bit de sinal). Se o primeiro operando for do tipo [uint](../keywords/uint.md) ou [ulong](../keywords/ulong.md), o deslocamento para a direita será um deslocamento lógico (bits de ordem superior são preenchidos com zero).

Tipos definidos pelo usuário podem sobrecarregar o operador `>>`; o tipo do primeiro operando deve ser o tipo definido pelo usuário e o tipo do segundo operando deve ser [int](../keywords/int.md). Para obter mais informações, consulte [operador](../keywords/operator.md). Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#26)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)