---
title: Explore os intervalos de dados usando intervalos e índices
description: Este tutorial avançado ensina você a explorar dados usando intervalos e índices para examinar fatias de um conjunto de dados sequencial.
ms.date: 09/20/2019
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: bbf3f257db9079c4f69f25c9ea08e7711b5ea04b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039665"
---
# <a name="indices-and-ranges"></a>Índices e intervalos

Intervalos e índices fornecem uma sintaxe sucinta para acessar elementos únicos ou intervalos em uma sequência.

Neste tutorial, você aprenderá a:

> [!div class="checklist"]
>
> - Use a sintaxe para intervalos em uma sequência.
> - Compreenda as decisões de design para o início e o fim de cada sequência.
> - Conheça cenários para os tipos <xref:System.Index> e <xref:System.Range>.

## <a name="language-support-for-indices-and-ranges"></a>Suporte a idioma para intervalos e índices

Esse suporte a idioma depende de dois novos tipos e de dois novos operadores:

- <xref:System.Index?displayProperty=nameWithType> representa um índice em uma sequência.
- O índice do operador end `^`, que especifica que um índice é relativo ao final de uma sequência.
- <xref:System.Range?displayProperty=nameWithType> representa um subintervalo de uma sequência.
- O operador Range `..`, que especifica o início e o término de um intervalo como seus operandos.

Vamos começar com as regras para índices. Considere uma matriz `sequence`. O índice `0` é o mesmo que `sequence[0]`. O índice `^0` é o mesmo que `sequence[sequence.Length]`. Observe que `sequence[^0]` gera uma exceção, assim como `sequence[sequence.Length]` faz. Para qualquer número `n`, o índice `^n` é o mesmo que `sequence[sequence.Length - n]`.

```csharp
string[] words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

Você pode recuperar a última palavra com o índice `^1`. Adicione o código a seguir abaixo da inicialização:

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Um intervalo especifica o *início* e o *final* de um intervalo. Intervalos são exclusivos, o que significa que *final* não está incluído no intervalo. O intervalo `[0..^0]` representa todo o intervalo, assim como `[0..sequence.Length]` representa todo o intervalo. 

O código a seguir cria um subintervalo com as palavras "quick", "brown" e "fox". Ele inclui `words[1]` até `words[3]`. O elemento `words[4]` não está no intervalo. Adicione o seguinte código ao mesmo método. Copie e cole-o na parte inferior da janela interativa.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

O código a seguir cria um subintervalo com "lazy" e "dog". Ele inclui `words[^2]` e `words[^1]`. O índice final `words[^0]` não está incluído. Adicione o seguinte código também:

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Os exemplos a seguir criam intervalos abertos para o início, fim ou ambos:

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Você também pode declarar intervalos ou índices como variáveis. A variável então pode ser usada dentro dos caracteres `[` e `]`:

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

O exemplo a seguir mostra muitos dos motivos para essas escolhas. Modifique `x`, `y` e `z` para tentar combinações diferentes. Quando você testar, use valores em que `x` é menor que `y` e `y` é menor que `z` para as combinações válidas. Adicione o seguinte código a um novo método. Tente usar combinações diferentes:

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Suporte de tipo para índices e intervalos

Se um tipo fornecer um [indexador](../programming-guide/indexers/index.md) com um parâmetro <xref:System.Index> ou <xref:System.Range>, ele dará suporte explicitamente a índices ou intervalos, respectivamente.

Um tipo é **contável** se tiver uma propriedade chamada `Length` ou `Count` com um getter acessível e um tipo de retorno de `int`. Um tipo com contagem que não dá suporte explicitamente a índices ou intervalos pode fornecer um suporte implícito para eles. Para obter mais informações, consulte as seções [suporte ao índice implícito](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) e [suporte de intervalo implícito](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) da [Nota de proposta de recurso](~/_csharplang/proposals/csharp-8.0/ranges.md).

Por exemplo, os seguintes tipos .NET oferecem suporte a índices e intervalos: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>e <xref:System.ReadOnlySpan%601>. O <xref:System.Collections.Generic.List%601> dá suporte a índices, mas não dá suporte a intervalos.

## <a name="scenarios-for-indices-and-ranges"></a>Cenários para índices e intervalos

Você muitas vezes usará intervalos e índices quando quiser executar uma análise no subintervalo de uma sequência inteira. A nova sintaxe é mais clara para ler exatamente quais subintervalo está envolvido. A função local `MovingAverage` usa um <xref:System.Range> como seu argumento. O método então enumera apenas esse intervalo ao calcular o mínimo, máximo e média. Experimente o seguinte código em seu projeto:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Baixe o código concluído no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes).
