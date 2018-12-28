---
title: Tuplas
description: Saiba mais sobre o F# tupla, um agrupamento de valores sem nomeados, mas ordenadas, possivelmente de diferentes tipos.
ms.date: 05/16/2016
ms.openlocfilehash: a1fc31d4dc97c0921545e53b91dcde0547002006
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611042"
---
# <a name="tuples"></a>Tuplas

Um *tupla* é um agrupamento de valores sem nomeados, mas ordenadas, possivelmente de diferentes tipos.  As tuplas podem ser tipos de referência ou structs.

## <a name="syntax"></a>Sintaxe

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>Comentários

Cada *elemento* na sintaxe anterior pode ser qualquer F# expressão.

## <a name="examples"></a>Exemplos

Pares de triplos e assim por diante, dos tipos iguais ou diferentes são exemplos de tuplas. Alguns exemplos são ilustrados no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>Obtendo valores individuais

Você pode usar a correspondência de padrões para acessar e atribuir nomes de elementos de tupla, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Você também pode desconstruir uma tupla por meio de correspondência de fora de um `match` expressão por meio de `let` associação:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Você pode padrão or corresponder na tuplas como entradas para funções:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Se você precisar apenas um elemento da tupla, o caractere curinga (sublinhado) pode ser usado para evitar a criação de um novo nome para um valor que não é necessário.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Copiando elementos de uma tupla de referência em uma tupla de struct também é simple:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

As funções `fst` e `snd` (referenciar apenas tuplas) retornar o primeiro e segundo os elementos de uma tupla, respectivamente.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Não há nenhuma função interna que retorna o terceiro elemento de um triplo, mas você pode facilmente escrever um da seguinte maneira.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

Em geral, é melhor usar a correspondência de padrões para acessar os elementos de tupla individuais.

## <a name="using-tuples"></a>Uso de tuplas

As tuplas fornecem uma maneira conveniente para retornar vários valores de uma função, conforme mostrado no exemplo a seguir. Este exemplo executa a divisão de inteiro e retorna o resultado arredondado da operação como membro de um par de tupla primeiro e o restante como um segundo membro do par.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

As tuplas também podem ser usadas como argumentos de função quando você quer evitar currying implícita dos argumentos de função implícita a sintaxe da função normal.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

A sintaxe normal para definir a função `let sum a b = a + b` permite que você defina uma função que é o aplicativo parcial do primeiro argumento da função, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

Usar uma tupla, como o parâmetro desabilita currying. Para obter mais informações, consulte "Parcial dos argumentos de aplicativo" na [funções](functions/index.md).

## <a name="names-of-tuple-types"></a>Nomes de tipos de tupla

Quando você escreve o nome de um tipo que é uma tupla, você usar o `*` símbolo para separar os elementos. Para uma tupla que consiste em uma `int`, um `float`e um `string`, tais como `(10, 10.0, "ten")`, o tipo deve ser escrito da seguinte maneira.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>Interoperação com tuplas do c#

C# 7.0 introduziu tuplas para o idioma.  As tuplas no C# são structs e são equivalentes a tuplas de struct no F#.  Se você precisar interoperar com c#, você deve usar tuplas de struct.

Isso é fácil de fazer.  Por exemplo, imagine que você precisa passar uma tupla a uma classe c# e, em seguida, consumir seu resultado, que também é uma tupla:

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

No seu F# código, você pode passar uma tupla de struct como parâmetro e consumir o resultado como uma tupla de struct.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Convertendo entre tuplas de referência e tuplas de Struct

Como as tuplas de referência e Tuples de Struct têm uma representação subjacente completamente diferente, eles não são implicitamente conversíveis.  Ou seja, não será compilado código como o seguinte:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Você deve padrão correspondem em uma tupla e construir o outro com as partes constituintes.  Por exemplo:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Forma compilada de tuplas de referência

Esta seção explica a forma de tuplas quando eles serão compilados.  As informações fornecidas aqui não não necessária para ler a menos que você tiver como alvo o .NET Framework 3.5 ou inferior.

As tuplas são compiladas em objetos de um dos vários tipos genéricos, todas nomeados `System.Tuple`, que são sobrecarregados na arity ou número de parâmetros de tipo. Tipos de tupla aparecem neste formulário quando você exibi-los de outra linguagem, tais como C# ou Visual Basic, ou quando você estiver usando uma ferramenta que não está ciente do F# constrói. O `Tuple` tipos foram introduzidos no .NET Framework 4. Se você estiver selecionando uma versão anterior do .NET Framework, o compilador usa as versões do [System. Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) da versão 2.0 do F# biblioteca principal. Os tipos na biblioteca são usados apenas para aplicativos que direcionam o 2.0, 3.0 e 3.5 versões do .NET Framework. Encaminhamento de tipo é usado para garantir a compatibilidade binária entre o .NET Framework 2.0 e o .NET Framework 4 F# componentes.

### <a name="compiled-form-of-struct-tuples"></a>Forma compilada de tuplas de Struct

Tuplas de struct (por exemplo, `struct (x, y)`), são fundamentalmente diferente das tuplas de referência.  Eles são compilados no <xref:System.ValueTuple> tipo, sobrecarregado por arity ou o número de parâmetros de tipo.  Elas são equivalentes às [tuplas do c# 7.0](../../csharp/tuples.md) e [tuplas do Visual Basic 2017](../../visual-basic/programming-guide/language-features/data-types/tuples.md)e interoperar bidirecionalmente.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Tipos F#](fsharp-types.md)