---
title: 'Loops: expressão for...to'
description: Veja como o F# para... a expressão to é usada para iterar em um loop em um intervalo de valores de uma variável de loop.
ms.date: 05/16/2016
ms.openlocfilehash: 882b6e48dd09efcb57f7ef2f419e68a6c43393a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283912"
---
# <a name="loops-forto-expression"></a>Loops: expressão for...to

A expressão `for...to` é usada para iterar em um loop em um intervalo de valores de uma variável de loop.

## <a name="syntax"></a>Sintaxe

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Comentários

O tipo do identificador é inferido do tipo das expressões de *início* e *término* . Os tipos para essas expressões devem ser inteiros de 32 bits.

Embora tecnicamente uma expressão, `for...to` é mais semelhante a uma instrução tradicional em uma linguagem de programação imperativa. O tipo de retorno para a *expressão Body* deve ser `unit`. Os exemplos a seguir mostram vários usos da expressão `for...to`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

A saída do código anterior está a seguir.

```console
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Loops: `for...in` expressão](loops-for-in-expression.md)
- [Loops: `while...do` expressão](loops-while-do-expression.md)
