---
title: "Inferência de tipos (F#)"
description: "Saiba como o compilador F # infere os tipos de valores, variáveis, parâmetros e valores de retorno."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2d5fa4b1-732a-4d71-a62d-07f7ee79fe06
ms.openlocfilehash: c23954c0a0828cc7d2aae0553d37d5ee1dfbe152
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="type-inference"></a>Inferência de tipos

Este tópico descreve como o compilador F # infere os tipos de valores, variáveis, parâmetros e valores de retorno.

## <a name="type-inference-in-general"></a>Inferência de tipo em geral
A ideia de inferência de tipo é que você não precisa especificar os tipos de F # construções exceto quando o compilador definitivamente não é possível deduzir o tipo. Omitir informações de tipo explícito não significa que F # é uma linguagem digitada dinamicamente ou se os valores em F # são fraco digitado. F # é uma linguagem estaticamente digitada, o que significa que o compilador deduz um tipo exato para cada construção durante a compilação. Se não houver informações suficientes para o compilador deduzir os tipos de cada construção, você deve fornecer informações de tipo adicionais, normalmente, adicionando anotações de tipo explícito em algum lugar no código.


## <a name="inference-of-parameter-and-return-types"></a>Inferência de tipos de parâmetro e tipos de retorno
Em uma lista de parâmetros, você não precisa especificar o tipo de cada parâmetro. E ainda, F # é uma linguagem estaticamente digitada e, portanto, cada valor e expressão tem um tipo definido em tempo de compilação. Para os tipos que você não especificar explicitamente, o compilador infere o tipo com base no contexto. Se o tipo não é especificado, ele é inferido para ser genérico. Se o código usa um valor de forma inconsistente, de forma que haja não única do tipo inferido que atenda a todos os usos de um valor, que o compilador relata um erro.

O tipo de retorno de uma função é determinado pelo tipo da última expressão na função.

Por exemplo, no código a seguir, os tipos de parâmetro `a` e `b` e o tipo de retorno são inferidos para ser `int` porque o literal `100` é do tipo `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Você pode influenciar a inferência de tipo alterando os literais. Se você fizer o `100` um `uint32` acrescentando o sufixo `u`, os tipos de `a`, `b`, e o valor de retorno são inferidos para ser `uint32`.

Você também pode influenciar inferência de tipo usando outras construções que implicam restrições no tipo, como funções e métodos que funcionam com apenas um tipo específico.

Além disso, você pode aplicar as anotações de tipo explícito para parâmetros de método ou função ou variáveis em expressões, conforme mostrado nos exemplos a seguir. Ocorrer erros se ocorrerem conflitos entre as diferentes restrições.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Você também pode especificar explicitamente o valor de retorno de uma função, fornecendo uma anotação de tipo depois que todos os parâmetros.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Um caso comum em que uma anotação de tipo é útil em um parâmetro é quando o parâmetro é um tipo de objeto e você deseja usar um membro.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a>Generalização automática
Se o código de função não é dependente do tipo de um parâmetro, o compilador considera o parâmetro para ser genérico. Isso é chamado de *generalização automática*, e pode ser um auxílio avançado para escrever o código genérico sem aumentar a complexidade.

Por exemplo, a função a seguir combina dois parâmetros de qualquer tipo em uma tupla.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

O tipo é inferido para ser

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Informações adicionais
Inferência de tipo é descrita mais detalhadamente na especificação da linguagem F #.


## <a name="see-also"></a>Consulte também
[Generalização Automática](generics/automatic-generalization.md)
