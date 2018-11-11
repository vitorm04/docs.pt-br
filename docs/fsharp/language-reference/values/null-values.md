---
title: Valores nulos (F#)
description: Saiba como o valor nulo é usado na linguagem de programação F#.
ms.date: 05/16/2016
ms.openlocfilehash: 8751ac402c43ddb07fb62e08b6c6d5403cbe9acc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43787890"
---
# <a name="null-values"></a>Valores nulos

Este tópico descreve como o valor nulo é usado em F#.

## <a name="null-value"></a>Valor nulo

O valor nulo não é usado normalmente em F# para valores ou variáveis. No entanto, null é exibido como um valor anormal em determinadas situações. Se um tipo é definido em F#, null não é permitido como um valor comum, a menos que o [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) atributo é aplicado ao tipo. Se um tipo é definido em qualquer outra linguagem .NET, null é um valor possível, e quando você está interoperando com esses tipos, seu código F# podem ser encontrados valores nulos.

Para um tipo definido em F# e usado estritamente de F#, a única maneira de criar um valor nulo usando a biblioteca F# diretamente é usar [unchecked. defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) ou [array. zerocreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). No entanto, para um tipo de F# que é usado de outras linguagens .NET, ou se você estiver usando esse tipo com uma API que não é gravada no F#, como o .NET Framework, os valores nulos podem ocorrer.

Você pode usar o `option` tipo em F# quando você pode usar uma variável de referência com um valor nulo possíveis em outra linguagem .NET. Em vez de null, com um F# `option` tipo, você usa o valor da opção `None` se não houver nenhum objeto. Você usa o valor da opção `Some(obj)` com um objeto `obj` quando há um objeto. Para obter mais informações, consulte [opções](../options.md).

O `null` palavra-chave é uma palavra-chave válida na linguagem F#, e você precisará usá-lo quando você estiver trabalhando com APIs do .NET Framework ou outras APIs que são escritos em outra linguagem .NET. Duas situações em que talvez seja necessário um valor nulo são quando você chama uma API do .NET e passe um valor nulo como um argumento e ao interpretar o valor de retorno ou um parâmetro de saída de uma chamada de método do .NET.

Para passar um valor nulo para um método do .NET, basta usar o `null` palavra-chave no código de chamada. O exemplo de código a seguir ilustra isso.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Para interpretar um valor nulo que é obtido de um método do .NET, use a correspondência de padrões, se possível. O exemplo de código a seguir mostra como usar a correspondência de padrões para interpretar o valor nulo que é retornado de `ReadLine` quando ele tenta ler após o término de um fluxo de entrada.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Valores nulos para tipos de F# também podem ser gerados de outras maneiras, como quando você usa `Array.zeroCreate`, que chama `Unchecked.defaultof`. Você deve ter cuidado com o código, para manter os valores nulos encapsulados. Em uma biblioteca destinada somente para F#, você não precisa verificar se há valores nulos em todas as funções. Se você estiver escrevendo uma biblioteca para interoperação com outras linguagens .NET, você talvez precise adicionar verificações para null, parâmetros de entrada e gerarem um `ArgumentNullException`, exatamente como faria em código c# ou Visual Basic.

Você pode usar o código a seguir para verificar se um valor arbitrário é nulo.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Consulte também

- [Valores](index.md)
- [Expressões Match](../match-expressions.md)
