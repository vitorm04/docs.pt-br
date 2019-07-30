---
title: Valores nulos
description: Saiba como o valor nulo é usado na linguagem F# de programação.
ms.date: 03/22/2019
ms.openlocfilehash: 2038c0a461fec9884c51edd50c3c9f336104e30e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630808"
---
# <a name="null-values"></a>Valores nulos

Este tópico descreve como o valor nulo é usado no F#.

## <a name="null-value"></a>Valor nulo

O valor nulo normalmente não é usado em F# para valores ou variáveis. No entanto, NULL aparece como um valor anormal em determinadas situações. Se um tipo for definido em F#, NULL não será permitido como um valor regular, a menos que o atributo [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) seja aplicado ao tipo. Se um tipo for definido em alguma outra linguagem .NET, NULL é um valor possível e, quando você estiver interoperante com esses tipos, F# seu código poderá encontrar valores nulos.

Para um tipo definido em F# e usado estritamente de F#, a única maneira de criar um valor nulo usando a F# biblioteca diretamente é usar Unchecked [. defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) ou [array. zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). No entanto, F# para um tipo que é usado de outras linguagens .net, ou se você estiver usando esse tipo com uma API que não F#é gravada no, como o .NET Framework, podem ocorrer valores nulos.

Você pode usar o `option` tipo em F# quando você pode usar uma variável de referência com um valor nulo possível em outra linguagem .net. Em vez de NULL, com F# `option` um tipo, você usará o `None` valor da opção se não houver nenhum objeto. Você usa o valor `Some(obj)` da opção com um objeto `obj` quando há um objeto. Para obter mais informações, veja [Opções](../options.md). Observe que você ainda pode empacotar `null` um valor em uma opção se, `Some x`para `x` , `null`for. Por isso, é importante que você use `None` quando um valor é. `null`

A `null` palavra-chave é uma palavra- F# chave válida no idioma e você precisa usá-la quando estiver trabalhando com APIs .NET Framework ou outras APIs que são escritas em outra linguagem .net. As duas situações nas quais você pode precisar de um valor nulo são quando você chama uma API .NET e passa um valor nulo como um argumento e quando você interpreta o valor de retorno ou um parâmetro de saída de uma chamada de método .NET.

Para passar um valor nulo para um método .net, basta usar a `null` palavra-chave no código de chamada. O exemplo de código a seguir ilustra isso.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Para interpretar um valor nulo que é obtido de um método .NET, use a correspondência de padrões, se possível. O exemplo de código a seguir mostra como usar a correspondência de padrões para interpretar o valor nulo que `ReadLine` é retornado quando ele tenta ler após o final de um fluxo de entrada.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Valores nulos F# para tipos também podem ser gerados de outras maneiras, como quando você usa `Array.zeroCreate`, que chama `Unchecked.defaultof`. Você deve ter cuidado com esse código para manter os valores nulos encapsulados. Em uma biblioteca destinada F#apenas ao, você não precisa verificar se há valores nulos em cada função. Se você estiver escrevendo uma biblioteca para interoperação com outras linguagens .net, talvez seja necessário adicionar verificações para parâmetros de entrada nulos e `ArgumentNullException`lançar um, assim como você C# faz no ou Visual Basic código.

Você pode usar o código a seguir para verificar se um valor arbitrário é nulo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Consulte também

- [Valores](index.md)
- [Expressões Match](../match-expressions.md)
