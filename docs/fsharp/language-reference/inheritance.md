---
title: Herança
description: Saiba como especificar F# relações de herança usando a palavra-chave 'inherit'.
ms.date: 05/16/2016
ms.openlocfilehash: 2fad2ddafbc0174903d3d24be3ce5412f7e1f9ed
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641816"
---
# <a name="inheritance"></a>Herança

Herança é usada para modelar a relação "é um" ou subtipagem na programação orientada a objeto.

## <a name="specifying-inheritance-relationships"></a>Especificando relações de herança

Especificar relações de herança usando o `inherit` palavra-chave em uma declaração de classe. A forma sintática básica é mostrada no exemplo a seguir.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Uma classe pode ter no máximo uma classe base direta. Se você não especificar uma classe base usando o `inherit` palavra-chave, a classe herda implicitamente de `System.Object`.

## <a name="inherited-members"></a>Membros herdados

Se uma classe herda de outra classe, os métodos e membros da classe base estão disponíveis para os usuários da classe derivada, como se fossem membros diretos da classe derivada.

Quaisquer associações let e parâmetros do construtor são particulares para uma classe e, portanto, não podem ser acessados de classes derivadas.

A palavra-chave `base` está disponível em classes derivadas e refere-se à instância de classe base. Ele é usado como o identificador de Self.

## <a name="virtual-methods-and-overrides"></a>Substituições e métodos virtuais

Métodos virtuais (e propriedades) funcionam de forma um pouco diferente em F# em comparação com outras linguagens .NET. Para declarar um novo membro virtual, você deve usar o `abstract` palavra-chave. Para fazer isso, independentemente se você fornecer uma implementação padrão para esse método. Portanto, uma definição completa de um método virtual em uma classe base segue este padrão:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

E, em uma classe derivada, uma substituição do método virtual segue este padrão:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Se você omitir a implementação padrão na classe base, a classe base se torna uma classe abstrata.

O exemplo de código a seguir ilustra a declaração de um novo método virtual `function1` em uma classe base e como substituí-la em uma classe derivada.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Construtores e herança

O construtor para a classe base deve ser chamado na classe derivada. Os argumentos para o construtor de classe base aparecem na lista de argumentos a `inherit` cláusula. Os valores que são usados devem ser determinados dos argumentos fornecidos para o construtor de classe derivada.

O código a seguir mostra uma classe base e uma classe derivada, em que a classe derivada chama o construtor de classe base na cláusula herdar:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

No caso de vários construtores, o código a seguir pode ser usado. A primeira linha dos construtores de classe derivada é o `inherit` cláusula e os campos aparecem como campos explícitos são declarados com o `val` palavra-chave. Para obter mais informações, consulte [campos explícitos: O `val` palavra-chave](members/explicit-fields-the-val-keyword.md).

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

## <a name="alternatives-to-inheritance"></a>Alternativas à herança

Em casos em que uma pequena modificação de um tipo é necessária, considere o uso de uma expressão de objeto como uma alternativa para herança. O exemplo a seguir ilustra o uso de uma expressão de objeto como uma alternativa para criar um novo tipo derivado:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Para obter mais informações sobre expressões de objeto, consulte [expressões do objeto](object-expressions.md).

Quando você estiver criando hierarquias de objeto, considere o uso de uma união discriminada em vez da herança. As uniões discriminadas também podem comportamento do modelo variado de objetos diferentes que compartilham um tipo geral comum. Uma união discriminada única pode muitas vezes eliminar a necessidade de um número de classes derivadas que são pequenas variações uns dos outros. Para obter informações sobre as uniões discriminadas, consulte [uniões discriminadas](discriminated-unions.md).

## <a name="see-also"></a>Consulte também

- [Expressões de Objeto](object-expressions.md)
- [Referência da Linguagem F#](index.md)
