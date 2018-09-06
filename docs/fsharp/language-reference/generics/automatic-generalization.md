---
title: Generalização automática (F#)
description: 'Saiba como F # automaticamente generaliza os argumentos e tipos de funções para que eles funcionem com vários tipos, quando possível.'
ms.date: 05/16/2016
ms.openlocfilehash: 84de9cbb2b9fcf2488393f7dbdfc3b610cdcffb0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855771"
---
# <a name="automatic-generalization"></a>Generalização automática

F # usa a inferência de tipo para avaliar os tipos de expressões e funções. Este tópico descreve como F # automaticamente generaliza os argumentos e tipos de funções para que eles funcionem com vários tipos de quando isso for possível.

## <a name="automatic-generalization"></a>Generalização automática

O compilador F #, quando ele executa a inferência de tipo em uma função, determina se um determinado parâmetro pode ser genérico. O compilador examina cada parâmetro e determina se a função tem uma dependência no tipo de parâmetro específico. Se não existir, o tipo é inferido para ser genérico.

O exemplo de código a seguir ilustra uma função que o compilador infere para ser genérico.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

O tipo é inferido para ser `'a -> 'a -> 'a`.

O tipo indica que se trata de uma função que leva dois argumentos do mesmo tipo desconhecido e retorna um valor do mesmo tipo. Um dos motivos que a função anterior pode ser genérico é que a maior-que o operador (`>`) em si for genérico. O maior-que o operador tem a assinatura `'a -> 'a -> bool`. Nem todos os operadores são genéricos e, se o código em uma função usa um tipo de parâmetro junto com uma função não genérica ou um operador, esse tipo de parâmetro não pode ser generalizado.

Porque `max` é genérico, ele pode ser usado com tipos, como `int`, `float`e assim por diante, conforme mostrado nos exemplos a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

No entanto, os dois argumentos devem ser do mesmo tipo. A assinatura é `'a -> 'a -> 'a`, e não `'a -> 'b -> 'a`. Portanto, o código a seguir produz um erro porque os tipos não coincidem.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

O `max` função também funciona com qualquer tipo que dá suporte à maior-que o operador. Portanto, você pode também usá-lo em uma cadeia de caracteres, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>Restrição de valor

O compilador executa a generalização automática apenas em definições de função completa com argumentos explícitos e simples valores imutáveis.

Isso significa que o compilador emitirá um erro se você tentar compilar o código que não é suficientemente restrito para ser um tipo específico, mas também não é generalizável. A mensagem de erro para esse problema se refere a essa restrição a generalização automática para valores como o *restrição de valor*.

Normalmente, o erro de restrição de valor ocorre quando você deseja uma construção para ser genérico, mas o compilador não tem informações suficientes para generalizá-la ou quando você omite não intencionalmente informações de tipo suficientes em um constructo não genérica. A solução para o erro de restrição de valor é fornecer informações mais explícitas para restringir mais completamente o problema de inferência de tipo, em uma das seguintes maneiras:

- Restringir um tipo seja não genérica ao adicionar uma anotação de tipo explícito para um valor ou parâmetro.

- Se o problema é usando um constructo de nongeneralizable para definir uma função genérica, como uma composição de função ou completamente aplicada a argumentos de função na forma curried, tente reescrever a função como uma definição de função comum.

- Se o problema é uma expressão que é muito complexa para ser generalizada, torná-lo em uma função adicionando um parâmetro extra e não utilizado.

- Adicione parâmetros de tipo genérico explícita. Essa opção raramente é usada.

- Os exemplos de código a seguir ilustram cada um desses cenários.

Caso 1: Uma expressão muito complexa. Neste exemplo, a lista `counter` se destina a ser `int option ref`, mas ele não está definido como um valor imutável simples.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Caso 2: Usando uma construção nongeneralizable para definir uma função genérica. Neste exemplo, a construção é nongeneralizable porque envolve a aplicação parcial dos argumentos da função.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Caso 3: Adicionando um parâmetro extra e não utilizado. Como essa expressão não é simple o suficiente para a generalização, o compilador emite o erro de restrição de valor.

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

Caso 4: Adicionando tipo parâmetros.

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

No último caso, o valor se torna um tipo de função, que pode ser usado para criar valores de vários tipos diferentes, por exemplo da seguinte maneira:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Consulte também

- [Inferência de Tipos](../type-inference.md)
- [Genéricos](index.md)
- [Parâmetros de Tipo Resolvidos Estaticamente](statically-resolved-type-parameters.md)
- [Restrições](constraints.md)
