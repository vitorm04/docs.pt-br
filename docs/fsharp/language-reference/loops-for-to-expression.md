---
title: 'Loops: expressão for...to (F#)'
description: 'Veja como o F # loop for... a expressão é usado para iterar em um loop em um intervalo de valores de uma variável de loop.'
ms.date: 05/16/2016
ms.openlocfilehash: 841c7d557abc11e0253cb87ab8081cc77671b44b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563396"
---
# <a name="loops-forto-expression"></a>Loops: expressão for...to

O `for...to` expressão é usada para iterar em um loop em um intervalo de valores de uma variável de loop.


## <a name="syntax"></a>Sintaxe

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Comentários
O tipo do identificador é inferido do tipo do *iniciar* e *concluir* expressões. Tipos para essas expressões devem ser inteiros de 32 bits.

Embora tecnicamente uma expressão, `for...to` é mais parecida com uma instrução tradicional em uma linguagem de programação imperativa. O tipo de retorno para o *corpo da expressão* devem ser `unit`. Os seguintes exemplos mostram vários usos do `for...to` expressão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

A saída do código anterior está a seguir.

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Loops: `for...in` expressão](loops-for-in-expression.md)

[Loops: `while...do` expressão](loops-while-do-expression.md)
