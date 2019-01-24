---
title: Operador &lt;&lt; – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: 79a48d88e2c83b5ad78804367ee3c07f78622c08
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333519"
---
# <a name="ltlt-operator-c-reference"></a>Operador &lt;&lt; (referência do C#)

O operador de deslocamento para a esquerda (`<<`) desloca o primeiro operando à esquerda pelo número de bits especificado pelo segundo operando. O tipo do segundo operando deve ser um [int](../keywords/int.md) ou um tipo que tem uma conversão numérica implícita predefinida para `int`.

## <a name="remarks"></a>Comentários

Se o primeiro operando for um [int](../keywords/int.md) ou [uint](../keywords/uint.md) (quantidade de 32 bits), a contagem de deslocamento será determinada pelos cinco bits de ordem inferior do segundo operando. Ou seja, a contagem real de deslocamento é de 0 a 31 bits.

Se o primeiro operando for um [long](../keywords/long.md) ou [ulong](../keywords/ulong.md) (quantidade de 64 bits), a contagem de deslocamento será determinada pelos seis bits de ordem inferior do segundo operando. Ou seja, a contagem real de deslocamento é de 0 a 63 bits.

Quaisquer bits de ordem superior que não estão dentro do intervalo do tipo do primeiro operando após a mudança são descartados e os bits vazios de ordem inferior são preenchidos com zeros. As operações de deslocamento nunca causam estouros.

Tipos definidos pelo usuário podem sobrecarregar o operador `<<` (consulte [operador](../keywords/operator.md)); o tipo do primeiro operando deve ser o tipo definido pelo usuário e o tipo do segundo operando deve ser `int`. Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#14)]

## <a name="comments"></a>Comentários

Observe que `i<<1` e `i<<33` fornecem o mesmo resultado, porque 1 e 33 têm os mesmos cinco bits de ordem inferior.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
