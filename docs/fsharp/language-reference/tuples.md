---
title: Tuplas (F#)
description: 'Saiba mais sobre F # tupla, um agrupamento de valores sem nome mas ordenados, possivelmente de tipos diferentes.'
ms.date: 05/16/2016
ms.openlocfilehash: d017a2ce8a6ad9b3cec8dfa2ee15b47f06d8f67c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564740"
---
# <a name="tuples"></a>Tuplas

Um *tupla* é um agrupamento de valores sem nome mas ordenados, possivelmente de tipos diferentes.  Tuplas podem ser tipos de referência ou estruturas.

## <a name="syntax"></a>Sintaxe

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a>Comentários
Cada *elemento* na sintaxe anterior pode ser qualquer expressão válida do F #.

## <a name="examples"></a>Exemplos
Exemplos de tuplas incluem pares, triplos e assim por diante, dos tipos iguais ou diferentes. Alguns exemplos estão ilustrados no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a>Obtendo valores individuais
Você pode usar a correspondência de padrões para acessar e atribuir nomes de elementos de tupla, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Você também pode decompor uma tupla por meio de correspondência de padrões fora de um `match` expressão via `let` associação:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Ou você pode padrão corresponder tuplas como entradas para funções:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Se você precisar de apenas um elemento de tupla, o caractere curinga (sublinhado) pode ser usado para evitar a criação de um novo nome para um valor que não é necessário.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Copiando elementos de uma tupla de referência em uma tupla de struct é simple:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

As funções `fst` e `snd` (referência apenas tuplas) retorna o primeiro e segundo elementos de uma tupla, respectivamente.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Não há nenhuma função interna que retorna o terceiro elemento de um triplo, mas você pode facilmente escrever um da seguinte maneira.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

Geralmente, é melhor usar a correspondência de padrão para acessar elementos de coleção de itens individuais.

## <a name="using-tuples"></a>Usando tuplas
Tuplas fornecem uma maneira conveniente para retornar vários valores de uma função, conforme mostrado no exemplo a seguir. Este exemplo executa a divisão de inteiro e retorna o resultado arredondado da operação como membro de um par de tupla primeiro e o restante como um segundo membro do par.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Tuplas também podem ser usadas como argumentos de função quando desejar evitar currying implícitos dos argumentos da função implícita a sintaxe de função normal.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

A sintaxe normal para definir a função `let sum a b = a + b` permite que você defina uma função que é o aplicativo parcial do primeiro argumento da função, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

Usando uma coleção de itens como o parâmetro desabilita currying. Para obter mais informações, consulte o "Aplicativo parcial de argumentos" [funções](functions/index.md).

## <a name="names-of-tuple-types"></a>Nomes de tipos de coleção de itens
Quando você escreve o nome de um tipo que é uma coleção de itens, você usar o `*` símbolo para separar elementos. Para uma tupla que consiste em uma `int`, um `float`e um `string`, como `(10, 10.0, "ten")`, o tipo deve ser escrito da seguinte maneira.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>Interoperação com c# tuplas

C# 7.0 introduzidos tuplas para o idioma.  Tuplas em c# são estruturas e são equivalentes a struct tuplas em F #.  Se você precisa interoperar com c#, você deve usar struct tuplas.

Isso é fácil.  Por exemplo, imagine que você precisa passar uma tupla a uma classe do c# e, em seguida, consumam seu resultado, o que também é uma coleção de itens:

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

No código F #, você pode passar uma tupla de estrutura como o parâmetro e consumir o resultado como uma tupla de struct.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Convertendo entre tuplas de referência e Struct tuplas

Como referência tuplas e Struct Tuples têm uma representação subjacente completamente diferente, eles não são implicitamente conversíveis.  Ou seja, não será compilado código como o seguinte:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Você deve padrão correspondem em uma tupla e construir o outro com as partes constituintes.  Por exemplo:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Forma compilada de tuplas de referência
Esta seção explica a forma de tuplas quando eles são compilados.  As informações aqui não são necessárias para ler a menos que o destino do .NET Framework 3.5 ou inferior.

Tuplas são compiladas em objetos de um dos vários tipos genéricos, todos os `System.Tuple`, que estão sobrecarregados no arity, ou o número de parâmetros de tipo. Tipos de coleção de itens aparecem neste formulário quando você exibi-las de outra linguagem, como c# ou Visual Basic, ou quando você estiver usando uma ferramenta que não está ciente das construções de linguagem F #. O `Tuple` tipos foram introduzidos no .NET Framework 4. Se tiver como alvo uma versão anterior do .NET Framework, o compilador usa versões do [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) da versão 2.0 da biblioteca principal F #. Os tipos na biblioteca são usados apenas para aplicativos voltados para o 2.0, 3.0 e 3.5 versões do .NET Framework. Encaminhamento de tipo é usado para garantir a compatibilidade binária entre os componentes do .NET Framework 2.0 e o .NET Framework 4 F #.

### <a name="compiled-form-of-struct-tuples"></a>Forma compilada do Struct tuplas

Struct tuplas (por exemplo, `struct (x, y)`), são fundamentalmente diferente da referência tuplas.  Eles são compilados no <xref:System.ValueTuple> tipo, sobrecarregado por arity ou o número de parâmetros de tipo.  Elas são equivalentes a [c# 7.0 tuplas](../../csharp/tuples.md) e [Visual Basic 2017 tuplas](../../visual-basic/programming-guide/language-features/data-types/tuples.md)e interoperem bidirecionalmente.

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Tipos F#](fsharp-types.md)
