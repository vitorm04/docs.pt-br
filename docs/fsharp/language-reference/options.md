---
title: Opções
description: Saiba como usar F# tipos de opção quando um valor real pode não existir para um valor ou uma variável nomeada.
ms.date: 05/16/2016
ms.openlocfilehash: 9326cf04f53adac7422c09a49a59c4eecd49486d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627355"
---
# <a name="options"></a>Opções

O tipo de opção F# em é usado quando um valor real pode não existir para um valor ou uma variável nomeada. Uma opção tem um tipo subjacente e pode conter um valor desse tipo, ou pode não ter um valor.

## <a name="remarks"></a>Comentários

O código a seguir ilustra uma função que gera um tipo de opção.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Como você pode ver, se a entrada `a` for maior que 0, `Some(a)` será gerada.  Caso contrário `None` , será gerado.

O valor `None` é usado quando uma opção não tem um valor real. Caso contrário, a `Some( ... )` expressão fornecerá a opção um valor. Os valores `Some` e `None` são úteis na correspondência de padrões, como na função `exists`a seguir, que `true` retorna se a opção tem um valor `false` e se não tem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Usando opções

As opções são usadas normalmente quando uma pesquisa não retorna um resultado correspondente, conforme mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

No código anterior, uma lista é pesquisada recursivamente. A função `tryFindMatch` usa uma função `pred` de predicado que retorna um valor booliano e uma lista a ser pesquisada. Se um elemento que satisfizer o predicado for encontrado, a recursão terminará e a função retornará o valor como uma `Some(head)`opção na expressão. A recursão termina quando a lista vazia é correspondida. Nesse ponto, o valor `head` não foi encontrado e `None` é retornado.

Muitas F# funções de biblioteca que pesquisam uma coleção de um valor que pode ou não existir retornam o `option` tipo. Por convenção, essas funções começam com o `try` prefixo, por exemplo, [`Seq.tryFindIndex`](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).

As opções também podem ser úteis quando um valor pode não existir, por exemplo, se for possível que uma exceção seja lançada quando você tentar construir um valor. O exemplo de código a seguir ilustra isso.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

A `openFile` função no exemplo anterior tem tipo `string -> File option` , pois ela retornará um `File` objeto se o arquivo for aberto com êxito `None` e se ocorrer uma exceção. Dependendo da situação, talvez não seja uma opção de design apropriada para capturar uma exceção em vez de permitir que ela se propague.

Além disso, ainda é possível passar `null` ou um valor que seja nulo para o `Some` caso de uma opção. Isso geralmente é evitado e normalmente está em programação rotineira F# , mas é possível devido à natureza dos tipos de referência no .net.

## <a name="option-properties-and-methods"></a>Métodos e propriedades de opção

O tipo de opção oferece suporte às propriedades e métodos a seguir.

|Propriedade ou método|Tipo|Descrição|
|------------------|----|-----------|
|[Nenhum](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|Uma propriedade estática que permite que você crie um valor de opção com o `None` valor.|
|[IsNone](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|Retorna `true` se a opção tem o `None` valor.|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|Retorna `true` se a opção tem um valor que não `None`é.|
|[Qualquer](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|Um membro estático que cria uma opção que tem um valor que não `None`é.|
|[Valor](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|Retorna o valor subjacente ou gera um `System.NullReferenceException` se o valor for. `None`|

## <a name="option-module"></a>Módulo de opção

Há um módulo, [opção](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c), que contém funções úteis que executam operações em opções. Algumas funções repetim a funcionalidade das propriedades, mas são úteis em contextos onde uma função é necessária. [Option. issome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79) e [Option. IsNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819) são ambas funções de módulo que testam se uma opção contém um valor. [Opção. Get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea) Obtém o valor, se houver um. Se não houver nenhum valor, ele será `System.ArgumentException`acionado.

A função [Option. bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0) executa uma função no valor, se houver um valor. A função deve usar exatamente um argumento e seu tipo de parâmetro deve ser o tipo de opção. O valor de retorno da função é outro tipo de opção.

O módulo de opção também inclui funções que correspondem às funções que estão disponíveis para listas, matrizes, sequências e outros tipos de coleção. Essas funções incluem [`Option.map`](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622) [`Option.iter`](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191) [,,`Option.fold`](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8), [`Option.exists`](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99) [,,`Option.count`](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876)e. [`Option.foldBack`](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb) [`Option.forall`](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428) Essas funções permitem que as opções sejam usadas como uma coleção de zero ou um elemento. Para obter mais informações e exemplos, consulte a discussão sobre funções de coleção em [listas](lists.md).

## <a name="converting-to-other-types"></a>Convertendo para outros tipos

As opções podem ser convertidas em listas ou matrizes. Quando uma opção é convertida em qualquer uma dessas estruturas de dados, a estrutura de dados resultante tem zero ou um elemento. Para converter uma opção em uma matriz, use [`Option.toArray`](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64). Para converter uma opção em uma lista, use [`Option.toList`](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Tipos F#](fsharp-types.md)
