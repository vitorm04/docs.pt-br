---
title: Inferência de tipos
description: Saiba como o F# compilador infere os tipos de valores, variáveis, parâmetros e valores de retorno.
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630185"
---
# <a name="type-inference"></a>Inferência de tipos

Este tópico descreve como o F# compilador infere os tipos de valores, variáveis, parâmetros e valores de retorno.

## <a name="type-inference-in-general"></a>Inferência de tipos em geral

A ideia da inferência de tipos é que você não precisa especificar os tipos de F# construções, exceto quando o compilador não pode deduzir de fato o tipo. Omitir informações de tipo explícito não significa que F# é uma linguagem com tipo dinâmico ou que os F# valores em são tipados de forma fraca. F#é uma linguagem digitada estaticamente, o que significa que o compilador deduz um tipo exato para cada construção durante a compilação. Se não houver informações suficientes para o compilador deduzir os tipos de cada construção, você deverá fornecer informações de tipo adicionais, normalmente Adicionando anotações de tipo explícitas em algum lugar no código.

## <a name="inference-of-parameter-and-return-types"></a>Inferência de tipos de parâmetro e de retorno

Em uma lista de parâmetros, não é necessário especificar o tipo de cada parâmetro. E, ainda F# , é uma linguagem com tipo estático e, portanto, cada valor e expressão tem um tipo definido em tempo de compilação. Para os tipos que você não especificar explicitamente, o compilador infere o tipo com base no contexto. Se o tipo não for especificado de outra forma, ele será inferido como genérico. Se o código usar um valor inconsistente, de forma que não haja nenhum tipo inferido único que satisfaça a todos os usos de um valor, o compilador relatará um erro.

O tipo de retorno de uma função é determinado pelo tipo da última expressão na função.

Por exemplo, no código a seguir, os `a` tipos de parâmetro e `b` e o tipo de retorno são `int` todos inferidos como sendo `100` o literal é `int`do tipo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Você pode influenciar a inferência de tipos alterando os literais. Se você fizer o `100` a `uint32` anexando o sufixo `u`, os tipos de `a` `uint32`, `b`e o valor de retorno serão inferidos como.

Você também pode influenciar a inferência de tipos usando outras construções que implicam restrições no tipo, como funções e métodos que funcionam com apenas um tipo específico.

Além disso, você pode aplicar anotações de tipo explícitas a parâmetros de função ou de método ou a variáveis em expressões, conforme mostrado nos exemplos a seguir. Erros resultam em caso de conflitos entre diferentes restrições.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Você também pode especificar explicitamente o valor de retorno de uma função fornecendo uma anotação de tipo após todos os parâmetros.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Um caso comum em que uma anotação de tipo é útil em um parâmetro é quando o parâmetro é um tipo de objeto e você deseja usar um membro.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a>Generalização automática

Se o código de função não for dependente do tipo de um parâmetro, o compilador considerará o parâmetro como genérico. Isso é chamado de *generalização automática*e pode ser uma grande ajuda para escrever código genérico sem aumentar a complexidade.

Por exemplo, a função a seguir combina dois parâmetros de qualquer tipo em uma tupla.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

O tipo é inferido para ser

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Informações adicionais

A inferência de tipos é descrita mais detalhadamente na especificação da F# linguagem.

## <a name="see-also"></a>Consulte também

- [Generalização Automática](./generics/automatic-generalization.md)
