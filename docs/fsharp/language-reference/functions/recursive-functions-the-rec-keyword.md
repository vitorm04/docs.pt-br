---
title: 'Funções recursivas: A palavra-chave REC'
description: Saiba como a F# palavra-chave ' Rec ' é usada com a palavra-chave ' Let ' para definir uma função recursiva.
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630659"
---
# <a name="recursive-functions-the-rec-keyword"></a>Funções recursivas: A palavra-chave REC

A `rec` palavra-chave é usada junto `let` com a palavra-chave para definir uma função recursiva.

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

Funções recursivas, funções que chamam a si mesmas, são identificadas explicitamente no F# idioma. Isso torna o identificador que está sendo definido disponível no escopo da função.

O código a seguir ilustra uma função recursiva que computa o número *n*<sup>ésimo</sup> Fibonacci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> Na prática, um código como esse acima é desperdício de memória e tempo do processador, pois envolve a recomputação de valores calculados anteriormente.

Os métodos são recursivos implicitamente dentro do tipo; Não é necessário adicionar a `rec` palavra-chave. Permitir que associações dentro de classes não sejam recursivas implicitamente.

## <a name="mutually-recursive-functions"></a>Funções recursivas mutuamente

Às vezes, as funções são recursivas *mutuamente*, o que significa que as chamadas formam um círculo, em que uma função chama outra que, por sua vez, chama a primeira, com qualquer número de chamadas entre elas. Você deve definir essas funções juntas em uma `let` associação, usando a `and` palavra-chave para vinculá-las.

O exemplo a seguir mostra duas funções recursivas mutuamente.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Consulte também

- [Funções](index.md)
