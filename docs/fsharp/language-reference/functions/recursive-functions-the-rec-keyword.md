---
title: 'Funções recursivas: a palavra-chave rec'
description: "Saiba como a palavra-chave ' Rec ' do F # é usada com a palavra-chave ' Let ' para definir uma função recursiva."
ms.date: 05/16/2016
ms.openlocfilehash: c9a3b7dc27f4ed86948a08b7783d7e8e8b60e57f
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87426970"
---
# <a name="recursive-functions-the-rec-keyword"></a>Funções recursivas: a palavra-chave rec

A `rec` palavra-chave é usada junto com a `let` palavra-chave para definir uma função recursiva.

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

Funções recursivas, funções que chamam a si mesmas, são identificadas explicitamente na linguagem F #. Isso torna o identificador que está sendo definido disponível no escopo da função.

O código a seguir ilustra uma função recursiva que computa o número *n*<sup>th</sup> Fibonacci usando a definição matemática.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> Na prática, um código como o exemplo anterior não é ideal porque ele unecessarily Recomputa os valores que já foram computados. Isso ocorre porque não é a cauda recursiva, o que é explicado mais adiante neste artigo.

Os métodos são recursivos implicitamente dentro do tipo; Não é necessário adicionar a `rec` palavra-chave. Permitir que associações dentro de classes não sejam recursivas implicitamente.

## <a name="tail-recursion"></a>Recursão final

Para algumas funções recursivas, é necessário refatorar uma definição mais "pura" para uma que seja a [cauda recursiva](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion). Isso impede os recálculos de desnecessários. Por exemplo, o gerador de número de Fibonacci anterior pode ser reescrito da seguinte maneira:

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

Essa é uma implementação mais complicada. Gerar um número Fibonacci é um ótimo exemplo de um algoritmo "simples", que é matematicamente puro, mas ineficiente na prática. Vários aspectos o tornam eficiente em F # enquanto ainda restam definidos recursivamente:

* Uma função interna recursiva chamada `loop` , que é um padrão idiomática F #.
* Dois parâmetros de acumulador, que passam valores de acumulação para chamadas recursivas.
* Uma verificação no valor de `n` para retornar uma acumulação específica.

Se este exemplo tiver sido escrito iterativamente com um loop, o código seria semelhante com dois valores diferentes acumulando números até que uma determinada condição fosse atendida.

O motivo pelo qual isso é a cauda-recursiva é porque a chamada recursiva não precisa salvar nenhum valor na pilha de chamadas. Todos os valores intermediários que estão sendo calculados são acumulados por meio de entradas para a função interna. Isso também permite que o compilador F # Otimize o código para ser tão rápido quanto se você tivesse escrito algo como um `while` loop.

É comum escrever código F # que processa recursivamente algo com uma função interna e externa, como mostra o exemplo anterior. A função interna usa a recursão de cauda, enquanto a função externa tem uma interface melhor para chamadores.

## <a name="mutually-recursive-functions"></a>Funções recursivas mutuamente

Às vezes, as funções são *recursivas mutuamente*, o que significa que as chamadas formam um círculo, em que uma função chama outra que, por sua vez, chama a primeira, com qualquer número de chamadas entre elas. Você deve definir essas funções juntas em uma `let` associação, usando a `and` palavra-chave para vinculá-las.

O exemplo a seguir mostra duas funções recursivas mutuamente.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Veja também

- [Funções](index.md)
