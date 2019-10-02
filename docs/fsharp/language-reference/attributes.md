---
title: Atributos
description: Saiba como F# os atributos permitem que os metadados sejam aplicados a um constructo de programação.
ms.date: 05/16/2016
ms.openlocfilehash: 17822891109b8e8eaa10044f82f0b872ce9d30b5
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736807"
---
# <a name="attributes"></a>Atributos

Os atributos permitem que os metadados sejam aplicados a um constructo de programação.

## <a name="syntax"></a>Sintaxe

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, o *destino* é opcional e, se presente, especifica o tipo de entidade de programa à qual o atributo se aplica. Os valores válidos para *destino* são mostrados na tabela que aparece mais adiante neste documento.

O *atributo-nome* refere-se ao nome (possivelmente qualificado com namespaces) de um tipo de atributo válido, com ou sem `Attribute` o sufixo que geralmente é usado em nomes de tipo de atributo. Por exemplo, o tipo `ObsoleteAttribute` pode ser reduzido para apenas `Obsolete` neste contexto.

Os *argumentos* são os argumentos para o construtor para o tipo de atributo. Se um atributo tiver um construtor sem parâmetros, a lista de argumentos e os parênteses poderão ser omitidos. Os atributos dão suporte a argumentos posicionais e argumentos nomeados. *Argumentos posicionais* são argumentos que são usados na ordem em que aparecem. Argumentos nomeados podem ser usados se o atributo tiver propriedades públicas. Você pode defini-los usando a sintaxe a seguir na lista de argumentos.

```fsharp
property-name = property-value
```

Essas inicializações de propriedade podem estar em qualquer ordem, mas devem seguir quaisquer argumentos posicionais. Veja a seguir um exemplo de um atributo que usa argumentos posicionais e inicializações de propriedade:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

Neste exemplo, o atributo é `DllImportAttribute`, aqui, usado na forma abreviada. O primeiro argumento é um parâmetro posicional e o segundo é uma propriedade.

Os atributos são uma construção de programação .NET que permite que um objeto conhecido como *atributo* seja associado a um tipo ou outro elemento de programa. O elemento Program ao qual um atributo é aplicado é conhecido como o *destino do atributo*. O atributo geralmente contém metadados sobre seu destino. Nesse contexto, os metadados podem ser qualquer dado sobre o tipo que não seja seus campos e membros.

Os atributos F# in podem ser aplicados às seguintes construções de programação: funções, métodos, assemblies, módulos, tipos (classes, registros, estruturas, interfaces, delegados, enumerações, uniões e assim por diante), construtores, propriedades, campos, parâmetros, parâmetros de tipo e valores de retorno. Atributos não são permitidos em `let` associações dentro de classes, expressões ou expressões de fluxo de trabalho.

Normalmente, a declaração de atributo aparece diretamente antes da declaração do destino do atributo. Várias declarações de atributo podem ser usadas juntas, da seguinte maneira:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

Você pode consultar atributos em tempo de execução usando a reflexão do .NET.

Você pode declarar vários atributos individualmente, como no exemplo de código anterior, ou pode declará-los em um conjunto de colchetes se usar um ponto e vírgula para separar os atributos e construtores individuais, da seguinte maneira:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Normalmente, os atributos encontrados `Obsolete` incluem o atributo, os atributos para considerações de segurança, atributos para suporte com, atributos relacionados à propriedade de código e atributos que indicam se um tipo pode ser serializado. O exemplo a seguir demonstra o uso do `Obsolete` atributo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Para os destinos `assembly` de atributo `module`e, você aplica os atributos a uma associação de `do` nível superior em seu assembly. Você pode incluir a palavra `assembly` ou `module` na declaração de atributo, da seguinte maneira:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Se você omitir o destino de atributo para um atributo aplicado `do` a uma associação F# , o compilador tentará determinar o destino do atributo que faz sentido para esse atributo. Muitas classes de atributo têm um atributo de `System.AttributeUsageAttribute` tipo que inclui informações sobre os possíveis destinos com suporte para esse atributo. Se o `System.AttributeUsageAttribute` indicar que o atributo dá suporte a funções como destinos, o atributo será levado para ser aplicado ao ponto de entrada principal do programa. Se o `System.AttributeUsageAttribute` indicar que o atributo dá suporte a assemblies como destinos, o compilador usa o atributo para aplicar ao assembly. A maioria dos atributos não se aplica a funções e assemblies, mas nos casos em que eles fazem, o atributo é levado para ser aplicado à função main do programa. Se o atributo target for especificado explicitamente, o atributo será aplicado ao destino especificado.

Embora você normalmente não precise especificar o destino do atributo explicitamente, os valores válidos para o *destino* em um atributo juntamente com exemplos de uso são mostrados na tabela a seguir:

<table>
  <tr>
    <th>Destino do atributo</td>
    <th>Exemplo</td> 
  </tr>
  <tr>
    <td>assembly</td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]</code></pre></td> 
  </tr>
  <tr>
    <td>return</td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1</code></pre></td> 
  </tr>
  <tr>
    <td>campo</td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int</code></pre></td> 
  </tr>
  <tr>
    <td>propriedade</td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x</code></pre></td> 
  </tr>
  <tr>
    <td>param</td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td> 
  </tr>
  <tr>
    <td>type</td>
    <td>
        <pre lang="fsharp"><code>
[&lt;type: StructLayout(Sequential)&gt;] 
type MyStruct = 
struct 
x : byte
y : int
end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
