---
title: Atributos (F#)
description: 'Saiba como habilitar o F # atributos metadados a ser aplicado a uma construção de programação.'
ms.date: 05/16/2016
ms.openlocfilehash: 107f5d9cbcce28c97fc5b738759ef27649fc45a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565419"
---
# <a name="attributes"></a>Atributos

Atributos habilitam metadados a ser aplicado a uma construção de programação.

## <a name="syntax"></a>Sintaxe

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, o *destino* é opcional e, se presente, especifica o tipo de entidade de programa que o atributo se aplica ao. Os valores válidos para *destino* são mostrados na tabela mostrada posteriormente neste documento.

O *nome do atributo* refere-se ao nome (possivelmente qualificado com namespaces) de um tipo de atributo válido, com ou sem o sufixo `Attribute` que geralmente é usado em nomes de tipo de atributo. Por exemplo, o tipo `ObsoleteAttribute` pode ser reduzido para apenas `Obsolete` neste contexto.

O *argumentos* são os argumentos para o construtor para o tipo de atributo. Se um atributo tem um construtor padrão, a lista de argumentos e parênteses podem ser omitidos. Suportam a atributos argumentos posicionais e argumentos nomeados. *Argumentos posicionais* são argumentos que são usados na ordem em que aparecem. Argumentos nomeados podem ser usados se o atributo tem propriedades públicas. Você pode definir essas configurações usando a sintaxe a seguir na lista de argumentos.

```
*property-name* = *property-value*
```

Tais inicializações de propriedade podem estar em qualquer ordem, mas eles devem seguir argumentos posicionais. A seguir está um exemplo de um atributo que usa argumentos posicionais e inicializações de propriedade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

Neste exemplo, o atributo é `DllImportAttribute`, aqui é usado em forma abreviada. O primeiro argumento é um parâmetro posicional e o segundo é uma propriedade.

Os atributos são uma construção de programação do .NET que permite que um objeto conhecido como um *atributo* a ser associado um tipo ou outro elemento do programa. O elemento do programa para o qual um atributo é aplicado é conhecido como o *atributo de destino*. O atributo normalmente contém metadados sobre seu destino. Nesse contexto, metadados podem ser qualquer dados sobre o tipo diferente de seus campos e membros.

Atributos em F # podem ser aplicados para as seguintes construções de programação: funções, métodos, assemblies, módulos, tipos (classes, registros, estruturas, interfaces, delegados, enumerações, uniões e assim por diante), construtores, propriedades, campos, parâmetros, parâmetros de tipo e valores de retorno. Atributos não são permitidos em `let` associações dentro de classes, expressões ou expressões de fluxo de trabalho.

Normalmente, a declaração de atributo aparece diretamente antes da declaração do atributo de destino. Várias declarações de atributo podem ser usadas em conjunto, da seguinte maneira.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

Você pode consultar os atributos em tempo de execução por meio de reflexão do .NET.

Você pode declarar vários atributos individualmente, como no exemplo de código anterior, ou você pode declará-los em um conjunto de colchetes, se você usar um ponto e vírgula para separar os atributos individuais e construtores, conforme mostrado aqui.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Atributos encontrados normalmente incluem o `Obsolete` atributo, atributos de considerações de segurança, atributos de COM suporte, os atributos relacionados à propriedade de código e atributos que indica se um tipo pode ser serializado. O exemplo a seguir demonstra o uso do `Obsolete` atributo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Para os destinos de atributo `assembly` e `module`, aplicar os atributos para um nível superior `do` de associação no seu assembly. Você pode incluir a palavra `assembly` ou `module` na declaração de atributo, da seguinte maneira.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Se você omitir o atributo de destino para um atributo aplicado a um `do` de associação, o compilador F # tentará determinar o atributo de destino que faça sentido para o atributo. Muitas classes de atributo tem um atributo de tipo `System.AttributeUsageAttribute` que inclui informações sobre os destinos possíveis com suporte para esse atributo. Se o `System.AttributeUsageAttribute` indica que o atributo oferece suporte a funções como destinos, o atributo é necessário para aplicar ao ponto de entrada principal do programa. Se o `System.AttributeUsageAttribute` indica que o atributo oferece suporte a assemblies como destinos, o compilador usa o atributo a ser aplicado ao assembly. A maioria dos atributos não se aplicam às funções e assemblies, mas em casos em que eles fazem, o atributo é feito para aplicar a função principal do programa. Se o atributo de destino for especificado explicitamente, o atributo é aplicado ao destino especificado.

Embora normalmente não é necessário especificar o atributo de destino explicitamente, os valores válidos para *destino* em um atributo são mostrados na tabela a seguir, junto com exemplos de uso.

<table>
  <tr>
    <th>Atributo de destino</td>
    <th>Exemplo</td> 
  </tr>
  <tr>
    <td>assembly</td>
    <td>`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</td> 
  </tr>
  <tr>
    <td>return</td>
    <td>' permitem function1 x: [<return: Obsolete>] int = x + 1'</td> 
  </tr>
  <tr>
    <td>campo</td>
    <td>' [<field: DefaultValue>] x: int mutável val'</td> 
  </tr>
  <tr>
    <td>propriedade</td>
    <td>' [<property: Obsolete>] isso. MyProperty = x'</td> 
  </tr>
  <tr>
    <td>Param</td>
    <td>' membro isso. Meumetodo ([<param: Out>] x: ref<int>) = x: = 10'</td> 
  </tr>
  <tr>
    <td>tipo</td>
    <td>
        ```
        [<type: StructLayout(Sequential)>] Digite MyStruct = struct x: bytes y: int final ```
    </td> 
  </tr>
</table>

## <a name="see-also"></a>Consulte também

[Referência da Linguagem F#](index.md)
