---
title: Explore os intervalos de dados usando intervalos e índices
description: Este tutorial avançado ensina você a explorar dados usando intervalos e índices para examinar fatias de um conjunto de dados sequencial.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 27f4b90f130345dd10517a5de78c759066afdf07
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926646"
---
# <a name="indices-and-ranges"></a>Índices e intervalos

Intervalos e índices fornecem uma sintaxe sucinta para acessar elementos únicos ou intervalos em <xref:System.Array>, <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>. Esses recursos permitem uma sintaxe mais concisa e clara para acessar elementos únicos ou intervalos de elementos em uma sequência.

Neste tutorial, você aprenderá a:

> [!div class="checklist"]
>
> - Use a sintaxe para intervalos em uma sequência.
> - Compreenda as decisões de design para o início e o fim de cada sequência.
> - Conheça cenários para os tipos <xref:System.Index> e <xref:System.Range>.

## <a name="language-support-for-indices-and-ranges"></a>Suporte a idioma para intervalos e índices

Este suporte à linguagem depende de dois tipos novos e dois operadores novos.

- <xref:System.Index?displayProperty=nameWithType> representa um índice em uma sequência.
- O operador `^`, que especifica que um índice é relativo ao final de uma sequência.
- <xref:System.Range?displayProperty=nameWithType> representa um subintervalo de uma sequência.
- O operador Range (`..`), que especifica o início e o final de um intervalo como seus operandos.

Vamos começar com as regras para índices. Considere uma matriz `sequence`. O índice `0` é o mesmo que `sequence[0]`. O índice `^0` é o mesmo que `sequence[sequence.Length]`. Observe que `sequence[^0]` gera uma exceção, assim como `sequence[sequence.Length]` faz. Para qualquer número `n`, o índice `^n` é o mesmo que `sequence[sequence.Length - n]`.

```csharp-interactive
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

## <a name="scenarios-for-indices-and-ranges"></a>Cenários para Intervalos e Índices

Você muitas vezes usará intervalos e índices quando quiser executar uma análise no subintervalo de uma sequência inteira. A nova sintaxe é mais clara para ler exatamente quais subintervalo está envolvido. A função local `MovingAverage` usa um <xref:System.Range> como seu argumento. O método então enumera apenas esse intervalo ao calcular o mínimo, máximo e média. Experimente o seguinte código em seu projeto:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Baixe o código concluído no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes).
