---
title: Herança
description: Saiba como especificar as relações de herança F# usando a palavra-chave 'herdar'.
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400284"
---
# <a name="inheritance"></a>Herança

A herança é usada para modelar a relação "é-a", ou subtipagem, na programação orientada a objetos.

## <a name="specifying-inheritance-relationships"></a>Especificando relações de herança

Você especifica relacionamentos de `inherit` herança usando a palavra-chave em uma declaração de classe. A forma sintática básica é mostrada no exemplo a seguir.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Uma classe pode ter no máximo uma classe base direta. Se você não especificar uma `inherit` classe base usando a palavra-chave, a classe herda implicitamente de `System.Object`.

## <a name="inherited-members"></a>Membros herdados

Se uma classe herdar de outra classe, os métodos e membros da classe base estão disponíveis para os usuários da classe derivada como se fossem membros diretos da classe derivada.

Quaisquer vinculações e parâmetros de construção são privados para uma classe e, portanto, não podem ser acessados a partir de classes derivadas.

A palavra-chave `base` está disponível em classes derivadas e refere-se à instância de classe base. É usado como o auto-identificador.

## <a name="virtual-methods-and-overrides"></a>Métodos e Substituições Virtuais

Os métodos virtuais (e propriedades) funcionam de forma um pouco diferente em F# em comparação com outros idiomas .NET. Para declarar um novo membro `abstract` virtual, use a palavra-chave. Você faz isso independentemente de fornecer uma implementação padrão para esse método. Assim, uma definição completa de um método virtual em uma classe base segue esse padrão:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

E em uma classe derivada, uma substituição deste método virtual segue esse padrão:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Se você omitir a implementação padrão na classe base, a classe base se tornará uma classe abstrata.

O exemplo de código a seguir ilustra `function1` a declaração de um novo método virtual em uma classe base e como substituí-lo em uma classe derivada.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Construtores e Herança

O construtor para a classe base deve ser chamado na classe derivada. Os argumentos para o construtor de classe base `inherit` aparecem na lista de argumentos na cláusula. Os valores utilizados devem ser determinados a partir dos argumentos fornecidos ao construtor de classe derivado.

O código a seguir mostra uma classe base e uma classe derivada, onde a classe derivada chama o construtor de classe base na cláusula de herança:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

No caso de vários construtores, o seguinte código pode ser usado. A primeira linha dos construtores de `inherit` classe derivadas é a cláusula, e os `val` campos aparecem como campos explícitos que são declarados com a palavra-chave. Para obter mais informações, consulte [Campos Explícitos: A `val` palavra-chave](./members/explicit-fields-the-val-keyword.md).

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a>Alternativas à Herança

Nos casos em que uma pequena modificação de um tipo é necessária, considere usar uma expressão de objeto como uma alternativa à herança. O exemplo a seguir ilustra o uso de uma expressão de objeto como alternativa à criação de um novo tipo derivado:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Para obter mais informações sobre expressões de objeto, consulte [Expressões de objeto](object-expressions.md).

Quando você estiver criando hierarquias de objetos, considere usar uma união discriminada em vez de herança. Sindicatos discriminados também podem modelar comportamentos variados de diferentes objetos que compartilham um tipo geral comum. Uma única união discriminada pode muitas vezes eliminar a necessidade de uma série de classes derivadas que são pequenas variações umas das outras. Para obter informações sobre sindicatos discriminados, consulte [Sindicatos Discriminados](discriminated-unions.md).

## <a name="see-also"></a>Confira também

- [Expressões de Objeto](object-expressions.md)
- [Referência de idioma F#](index.md)
