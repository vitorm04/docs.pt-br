---
title: Opções (F#)
description: 'Saiba como usar a opção de F # tipos quando um valor real podem não existir para um valor nomeado ou variável.'
ms.date: 05/16/2016
ms.openlocfilehash: c813c377af1db758a40efa2bd73de22cbb4c66f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="options"></a>Opções

O tipo de opção em F # é usado quando um valor real pode não existir para um valor nomeado ou variável. Uma opção tem um tipo subjacente e pode conter um valor desse tipo, ou pode não ter um valor.

## <a name="remarks"></a>Comentários
O código a seguir ilustra uma função que gera um tipo de opção.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Como você pode ver, se a entrada `a` é maior que 0, `Some(a)` é gerado.  Caso contrário, `None` é gerado.

O valor `None` é usado quando uma opção não tem um valor real. Caso contrário, a expressão `Some( ... )` permite que um valor. Os valores `Some` e `None` são úteis para correspondência de padrões, como a seguinte função `exists`, que retorna `true` se a opção tiver um valor e `false` se não existir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Usando opções
Opções são usadas quando uma pesquisa não retorna um resultado correspondente, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

No código anterior, uma lista é pesquisada recursivamente. A função `tryFindMatch` usa uma função de predicado `pred` que retorna um valor booliano e uma lista de pesquisa. Se um elemento que satisfaz o predicado for encontrado, a recursão será encerrada e a função retorna o valor como uma opção na expressão `Some(head)`. A recursão termina quando uma lista vazia for correspondida. Nesse ponto, o valor `head` não foi encontrado, e `None` é retornado.

Muitos F # funções de biblioteca que pesquisar uma coleção para um valor que pode ou não existir retornar o `option` tipo. Por convenção, essas funções começam com o `try` prefixo, por exemplo, [ `Seq.tryFindIndex` ](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).

Opções também podem ser úteis quando um valor pode não existir, por exemplo, se for possível que uma exceção será lançada quando você tenta construir um valor. O exemplo de código a seguir ilustra isso.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

O `openFile` função no exemplo anterior tem tipo `string -> File option` porque retorna um `File` se o arquivo é aberto com êxito do objeto e `None` se ocorrer uma exceção. Dependendo da situação, pode não ser uma opção de projeto apropriada para capturar uma exceção em vez de permitir sua propagação.


## <a name="option-properties-and-methods"></a>Métodos e propriedades de opção
O tipo de opção suporta as seguintes propriedades e métodos.



|Propriedade ou método|Tipo|Descrição|
|------------------|----|-----------|
|[Nenhum](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|Uma propriedade estática que permite que você crie um valor de opção que tenha o `None` valor.|
|[IsNone](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|Retorna `true` se a opção tem o `None` valor.|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|Retorna `true` se a opção tiver um valor que não seja `None`.|
|[Alguns](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|Um membro estático que cria uma opção que tem um valor que não seja `None`.|
|[Value](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|Retorna o valor subjacente ou lança uma `System.NullReferenceException` se o valor for `None`.|

## <a name="option-module"></a>Módulo de opção
Há um módulo, [opção](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c), que contém funções úteis que executam operações em Opções. Algumas funções de repetir a funcionalidade das propriedades, mas são úteis em contextos em que uma função é necessária. [Issome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79) e [isnone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819) são ambas as funções do módulo que testar se uma opção contém um valor. [Option.Get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea) obtém o valor, se houver um. Se não houver nenhum valor, ele lança `System.ArgumentException`.

O [Option](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0) função executa uma função no valor, se houver um valor. A função deve utilizar exatamente um argumento e seu tipo de parâmetro deve ser do tipo de opção. O valor de retorno da função é outro tipo de opção.

O módulo de opção também inclui funções que correspondem às funções que estão disponíveis para matrizes, listas, sequências e outros tipos de coleção. Essas funções incluem [ `Option.map` ](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622), [ `Option.iter` ](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191), [ `Option.forall` ](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428), [ `Option.exists` ](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99), [ `Option.foldBack` ](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb), [ `Option.fold` ](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8), e [ `Option.count` ](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876). Estas funções permitem opções a serem usadas como uma coleção de elementos de zero ou um. Para obter mais informações e exemplos, consulte a discussão sobre funções de coleção em [lista](lists.md).


## <a name="converting-to-other-types"></a>Converter em outros tipos
Opções podem ser convertidas em listas ou matrizes. Quando uma opção é convertida em qualquer uma dessas estruturas de dados, a estrutura de dados resultante tem zero ou um elemento. Para converter uma opção em uma matriz, use [ `Option.toArray` ](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64). Para converter uma opção em uma lista, use [ `Option.toList` ](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1).


## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Tipos F#](fsharp-types.md)
