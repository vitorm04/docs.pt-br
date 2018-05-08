---
title: 'Funções recursivas: a palavra-chave rec (F#)'
description: "Saiba como a palavra-chave F # 'rec' é usada com a palavra-chave 'let' para definir uma função recursiva."
ms.date: 05/16/2016
ms.openlocfilehash: 6039a48eae2b16aa1d82617176460d727a878d87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
Funções recursivas, funções que chamam, são identificadas explicitamente na linguagem F #. Isso disponibiliza o identificador que é definido no escopo da função.

O código a seguir ilustra uma função recursiva que calcula o *n*th Fibonacci número.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
Na prática, o código desse acima é desperdício de tempo do processador e memória porque ela envolve o recálculo de valores computados anteriormente.


Métodos são implicitamente recursiva dentro do tipo; não é necessário adicionar o `rec` palavra-chave. Associações Let em classes não são implicitamente recursiva.


## <a name="mutually-recursive-functions"></a>Funções mutuamente recursivas
Às vezes, são funções *mutuamente recursivas*, que significa que as chamadas formam um círculo, em que uma função chama outro que por sua vez, chama a primeira, com qualquer número de chamadas entre. Você deve definir essas funções juntas no `let` de associação, usando o `and` palavra-chave para vinculá-los juntos.

O exemplo a seguir mostra duas mutuamente funções recursivas.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Consulte também
[Funções](index.md)
