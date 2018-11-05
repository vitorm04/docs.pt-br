---
title: 'Funções recursivas: a palavra-chave rec (F#)'
description: "Saiba como a palavra-chave F # 'rec' é usada com a palavra-chave 'let' para definir uma função recursiva."
ms.date: 05/16/2016
ms.openlocfilehash: 5aab6ed8ab0fc3c0f0bcfc93c3ce6518ec53254f
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "48024513"
---
# <a name="recursive-functions-the-rec-keyword"></a>Funções recursivas: a palavra-chave rec

O `rec` palavra-chave é usada junto com o `let` palavra-chave para definir uma função recursiva.

## <a name="syntax"></a>Sintaxe

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a>Comentários

Funções recursivas, funções que chamam seu site, são identificadas explicitamente na linguagem F #. Isso disponibiliza o identificador que está sendo definido no escopo da função.

O código a seguir ilustra uma função recursiva que calcula a *n*<sup>th</sup> número Fibonacci.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
Na prática, o código acima como esse é um desperdício de tempo do processador e memória porque ela envolve o recálculo dos valores computados anteriormente.

Métodos são implicitamente recursivos dentro do tipo; não é necessário adicionar o `rec` palavra-chave. Associações Let em classes não são implicitamente recursivos.

## <a name="mutually-recursive-functions"></a>Funções mutuamente recursivas

Às vezes, são funções *mutuamente recursivas*, que significa que chamadas formam um círculo, em que uma função chama outra que por sua vez chama o primeiro, com qualquer número de chamadas entre os dois. Você deve definir essas funções juntas em um `let` vinculação, usando o `and` palavra-chave para vinculá-los.

O exemplo a seguir mostra dois mutuamente funções recursivas.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Consulte também

- [Funções](index.md)
