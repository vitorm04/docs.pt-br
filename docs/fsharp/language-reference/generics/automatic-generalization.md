---
title: Generalização automática
description: Saiba como F# generaliza automaticamente os argumentos e tipos de funções para que funcionem com vários tipos, quando possível.
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630629"
---
# <a name="automatic-generalization"></a>Generalização automática

F#usa inferência de tipos para avaliar os tipos de funções e expressões. Este tópico descreve como F# generaliza automaticamente os argumentos e tipos de funções para que funcionem com vários tipos quando isso for possível.

## <a name="automatic-generalization"></a>Generalização automática

O F# compilador, quando executa a inferência de tipos em uma função, determina se um determinado parâmetro pode ser genérico. O compilador examina cada parâmetro e determina se a função tem uma dependência no tipo específico desse parâmetro. Caso contrário, o tipo é inferido para ser genérico.

O exemplo de código a seguir ilustra uma função que o compilador infere para ser genérico.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

O tipo é inferido para ser `'a -> 'a -> 'a`.

O tipo indica que se trata de uma função que usa dois argumentos do mesmo tipo desconhecido e retorna um valor desse mesmo tipo. Um dos motivos pelos quais a função anterior pode ser genérica é que o operador maior que (`>`) é o próprio genérico. O operador maior que tem a assinatura `'a -> 'a -> bool`. Nem todos os operadores são genéricos e, se o código em uma função usar um tipo de parâmetro junto com uma função ou um operador não genérico, esse tipo de parâmetro não poderá ser generalizado.

Como o `int` `float`é genérico, ele pode ser usado com tipos como, e assim por diante, conforme mostrado nos exemplos a seguir. `max`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

No entanto, os dois argumentos devem ser do mesmo tipo. A assinatura é `'a -> 'a -> 'a`, não `'a -> 'b -> 'a`. Portanto, o código a seguir produz um erro porque os tipos não correspondem.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

A `max` função também funciona com qualquer tipo que dê suporte ao operador maior que. Portanto, você também pode usá-lo em uma cadeia de caracteres, conforme mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>Restrição de valor

O compilador executa a generalização automática somente em definições de função completas que têm argumentos explícitos e em valores imutáveis simples.

Isso significa que o compilador emite um erro se você tentar compilar o código que não está suficientemente restrito a ser um tipo específico, mas também não é generalizado. A mensagem de erro para esse problema refere-se a essa restrição na generalização automática para valores como a *restrição de valor*.

Normalmente, o erro de restrição de valor ocorre quando você deseja que uma construção seja genérica, mas o compilador não tem informações suficientes para generalizar ou quando você omite involuntariamente informações de tipo suficientes em uma construção não genérica. A solução para o erro de restrição de valor é fornecer informações mais explícitas para restringir completamente o problema de inferência de tipo, de uma das seguintes maneiras:

- Restringir um tipo a ser não genérico adicionando uma anotação de tipo explícita a um valor ou parâmetro.

- Se o problema estiver usando uma construção não generalizada para definir uma função genérica, como uma composição de função ou um argumento de função na forma curried aplicado de forma incompleta, tente reescrever a função como uma definição de função comum.

- Se o problema for uma expressão muito complexa para ser generalizada, torne-a uma função adicionando um parâmetro extra e não utilizado.

- Adicione parâmetros de tipo genérico explícito. Essa opção é raramente usada.

- Os exemplos de código a seguir ilustram cada um desses cenários.

Caso 1: Uma expressão muito complexa. Neste exemplo, a lista `counter` deve ser `int option ref`, mas não é definida como um valor imutável simples.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Caso 2: Usando uma construção não generalizada para definir uma função genérica. Neste exemplo, a construção é não generalizada porque envolve a aplicação parcial de argumentos de função.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Caso 3: Adicionando um parâmetro extra não utilizado. Como essa expressão não é simples o suficiente para generalização, o compilador emite o erro de restrição de valor.

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

Caso 4: Adicionando parâmetros de tipo.

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

No último caso, o valor se torna uma função de tipo, que pode ser usada para criar valores de vários tipos diferentes, por exemplo, da seguinte maneira:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Consulte também

- [Inferência de Tipos](../type-inference.md)
- [Genéricos](index.md)
- [Parâmetros de Tipo Resolvidos Estaticamente](statically-resolved-type-parameters.md)
- [Restrições](constraints.md)
