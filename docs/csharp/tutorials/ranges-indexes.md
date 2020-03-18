---
title: Explore os intervalos de dados usando intervalos e índices
description: Este tutorial avançado ensina você a explorar dados usando intervalos e índices para examinar fatias de um conjunto de dados sequencial.
ms.date: 03/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 82aad968e2efc437c82a7c8250bcd108b60b09e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156488"
---
# <a name="indices-and-ranges"></a>Índices e intervalos

Faixas e índices fornecem uma sintaxe sucinta para acessar elementos únicos ou intervalos em uma seqüência.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> - Use a sintaxe para intervalos em uma sequência.
> - Compreenda as decisões de design para o início e o fim de cada sequência.
> - Conheça cenários para os tipos <xref:System.Index> e <xref:System.Range>.

## <a name="language-support-for-indices-and-ranges"></a>Suporte a idioma para intervalos e índices

Este suporte ao idioma conta com dois novos tipos e dois novos operadores:

- <xref:System.Index?displayProperty=nameWithType> representa um índice em uma sequência.
- O índice do `^`operador final , que especifica que um índice é relativo ao fim de uma seqüência.
- <xref:System.Range?displayProperty=nameWithType> representa um subintervalo de uma sequência.
- O operador `..`de alcance , que especifica o início e o fim de uma faixa como seus operadores.

Vamos começar com as regras para índices. Considere uma matriz `sequence`. O índice `0` é o mesmo que `sequence[0]`. O índice `^0` é o mesmo que `sequence[sequence.Length]`. A `sequence[^0]` expressão faz uma exceção, assim como. `sequence[sequence.Length]` Para qualquer número `n`, o índice `^n` é o mesmo que `sequence[sequence.Length - n]`.

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

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Um intervalo especifica o *início* e o *final* de um intervalo. As faixas são exclusivas, o que significa que o *final* não está incluído na gama. O intervalo `[0..^0]` representa todo o intervalo, assim como `[0..sequence.Length]` representa todo o intervalo.

O código a seguir cria um subintervalo com as palavras "quick", "brown" e "fox". Ele inclui `words[1]` até `words[3]`. O elemento `words[4]` não está no intervalo. Adicione o seguinte código ao mesmo método. Copie e cole-o na parte inferior da janela interativa.

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

O código a seguir cria um subintervalo com "lazy" e "dog". Ele inclui `words[^2]` e `words[^1]`. O índice final `words[^0]` não está incluído. Adicione o seguinte código também:

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Os exemplos a seguir criam intervalos abertos para o início, fim ou ambos:

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Você também pode declarar intervalos ou índices como variáveis. A variável então pode ser usada dentro dos caracteres `[` e `]`:

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

O exemplo a seguir mostra muitos dos motivos para essas escolhas. Modifique `x`, `y` e `z` para tentar combinações diferentes. Quando você testar, use valores em que `x` é menor que `y` e `y` é menor que `z` para as combinações válidas. Adicione o seguinte código a um novo método. Tente usar combinações diferentes:

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Tipo suporte para índices e faixas

Índices e faixas fornecem sintaxe clara e concisa para acessar um único elemento ou uma subgama de elementos em uma seqüência. Uma expressão de índice normalmente retorna o tipo de elementos de uma seqüência. Uma expressão de intervalo normalmente retorna o mesmo tipo de seqüência da seqüência de origem.

Qualquer tipo que forneça um <xref:System.Index> <xref:System.Range> [indexador](../programming-guide/indexers/index.md) com um ou parâmetro suporta explicitamente índices ou faixas, respectivamente. Um indexador que <xref:System.Range> toma um único parâmetro pode <xref:System.Span%601?displayProperty=nameWithType>retornar um tipo de seqüência diferente, como .

Um tipo é **contável** se `Length` `Count` tiver uma propriedade nomeada ou `int`com um getter acessível e um tipo de retorno de . Um tipo contável que não suporta explicitamente índices ou intervalos pode fornecer um suporte implícito para eles. Para obter mais informações, consulte as seções [de suporte ao Índice Implícito](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) e à Faixa [Implícita](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) da [nota de proposta de recurso](~/_csharplang/proposals/csharp-8.0/ranges.md). Intervalos usando suporte de intervalo implícito retornam o mesmo tipo de seqüência que a seqüência de origem.

Por exemplo, os seguintes tipos .NET suportam índices e intervalos: <xref:System.String>, <xref:System.Span%601>e <xref:System.ReadOnlySpan%601>. Os <xref:System.Collections.Generic.List%601> índices suportam, mas não suportam faixas.

<xref:System.Array>tem um comportamento mais matizado. Os arrays de dimensões únicas suportam índices e intervalos. Matrizes multidimensionais não. O indexador para uma matriz multidimensional tem múltiplos parâmetros, não um único parâmetro. Os arrays irregulares, também referidos como uma matriz de matrizes, suportam ambos os intervalos e indexadores. O exemplo a seguir mostra como iterar uma subseção retangular de uma matriz irregular. Itenumera a seção no centro, excluindo a primeira e a última três linhas, e as duas primeiras e últimas duas colunas de cada linha selecionada:

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

## <a name="scenarios-for-indices-and-ranges"></a>Cenários para índices e faixas

Muitas vezes você usará intervalos e índices quando quiser analisar uma subgama de uma seqüência maior. A nova sintaxe é mais clara para ler exatamente quais subintervalo está envolvido. A função local `MovingAverage` usa um <xref:System.Range> como seu argumento. O método então enumera apenas esse intervalo ao calcular o mínimo, máximo e média. Experimente o seguinte código em seu projeto:

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
