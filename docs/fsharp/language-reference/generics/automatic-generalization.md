---
title: "Generalização automática (F#)"
description: "Saiba como F # automaticamente generaliza os argumentos e tipos de funções para que eles funcionem com vários tipos, quando possível."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 14a3554c-3fad-4eba-a93d-8ba07d1245b4
ms.openlocfilehash: d60831084cef76ce29f64322362b4920520f71d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="automatic-generalization"></a>Generalização automática

F # usa a inferência de tipo para avaliar os tipos de funções e expressões. Este tópico descreve como F # automaticamente generaliza os argumentos e tipos de funções para que eles funcionem com vários tipos, quando possível.


## <a name="automatic-generalization"></a>Generalização automática
O compilador F #, quando ele executa a inferência de tipo em uma função, determina se um determinado parâmetro pode ser genérico. O compilador examina cada parâmetro e determina se a função tem uma dependência no tipo específico de parâmetro. Se não estiver, o tipo é inferido para ser genérico.

O exemplo de código a seguir ilustra uma função que o compilador infere para ser genérico.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

O tipo é inferido para ser `'a -> 'a -> 'a`.

O tipo indica que se trata de uma função que leva dois argumentos do mesmo tipo desconhecido e retorna um valor do mesmo tipo. Um dos motivos que a função anterior pode ser genérico é que o maior-que o operador (`>`) é genérico. O maior-que o operador tem a assinatura `'a -> 'a -> bool`. Nem todos os operadores são genéricos e se o código em uma função usa um tipo de parâmetro junto com uma função não genérico ou operador, esse tipo de parâmetro não pode ser generalizado.

Porque `max` é genérico, ele pode ser usado com tipos como `int`, `float`e assim por diante, conforme mostrado nos exemplos a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

No entanto, os dois argumentos devem ser do mesmo tipo. A assinatura é `'a -> 'a -> 'a`, não `'a -> 'b -> 'a`. Portanto, o código a seguir produz um erro porque os tipos não correspondem.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

O `max` função também funciona com qualquer tipo que oferece suporte à maior-que o operador. Portanto, você também pode usá-lo em uma cadeia de caracteres, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a>Restrição de valor
O compilador executa generalização automática somente em definições de função completa com argumentos explícitos e valores imutáveis simples.

Isso significa que o compilador emite um erro se você tentar compilar o código que não é suficientemente restrito para ser um tipo específico, mas também não é generalizável. A mensagem de erro para esse problema se refere a essa restrição em generalização automática para valores como o *valor restrição*.

Normalmente, o erro de restrição de valor ocorre quando você deseja uma construção para ser genérico, mas o compilador não tem informações suficientes para generalizar ou quando você omitir acidentalmente informações suficientes do tipo em uma construção não genérica. A solução para o erro de restrição de valor é fornecer informações mais explícitas para restringir mais totalmente o problema de inferência de tipo, em uma das seguintes maneiras:


- Restringir um tipo a ser não-genérica pela adição de uma anotação de tipo explícito para um valor ou parâmetro.

- Se o problema está usando uma construção de nongeneralizable para definir uma função genérica, como uma composição de função ou completamente aplicada argumentos da função na forma curried, tente reescrever a função como uma definição de função comum.

- Se o problema é uma expressão que é muito complexa para ser generalizado, torne-o em uma função adicionando um parâmetro extra, não utilizado.

- Adicione parâmetros de tipo genérico explícito. Essa opção raramente é usada.

- Os exemplos de código a seguir ilustram cada um desses cenários.

Caso 1: Uma expressão muito complexa. Neste exemplo, a lista `counter` se destina a ser `int option ref`, mas ele não está definido como um valor imutável simples.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Caso 2: Uso da construção nongeneralizable para definir uma função genérica. Neste exemplo, a construção é nongeneralizable porque ela envolve a aplicação parcial de argumentos de função.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Caso 3: Adicionando um parâmetro extra, não utilizado. Como essa expressão não é simple o suficiente para generalização, o compilador emite o erro de restrição de valor.

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

No último caso, o valor torna-se um tipo de função, que pode ser usado para criar valores de vários tipos diferentes, por exemplo da seguinte maneira:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Consulte também
[Inferência de Tipos](../type-inference.md)

[Genéricos](index.md)

[Parâmetros de Tipo Resolvidos Estaticamente](statically-resolved-type-parameters.md)

[Restrições](constraints.md)

