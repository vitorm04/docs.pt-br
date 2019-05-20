---
title: Explore os intervalos de dados usando intervalos e índices
description: Este tutorial avançado ensina você a explorar dados usando intervalos e índices para examinar fatias de um conjunto de dados sequencial.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 64fae4581e265d4f70b8356d5c651b4fdaca3fe9
ms.sourcegitcommit: dd3b897feb5c4ac39732bb165848e37a344b0765
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/25/2019
ms.locfileid: "64431497"
---
# <a name="indices-and-ranges"></a>Índices e intervalos

Intervalos e índices fornecem uma sintaxe sucinta para acessar elementos únicos ou intervalos em <xref:System.Array>, <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>. Esses recursos permitem uma sintaxe mais concisa e clara para acessar elementos únicos ou intervalos de elementos em uma sequência.

Neste tutorial, você aprenderá a:

> [!div class="checklist"]
> * Use a sintaxe para intervalos em uma sequência.
> * Compreenda as decisões de design para o início e o fim de cada sequência.
> * Conheça cenários para os tipos <xref:System.Index> e <xref:System.Range>.

## <a name="language-support-for-indices-and-ranges"></a>Suporte a idioma para intervalos e índices

Você pode especificar um índice **do final** usando o caractere `^` antes do índice. A indexação do final começa da regra que `0..^0` especifica o intervalo inteiro. Para enumerar uma matriz inteira, você inicia *no primeiro elemento* e continua até você *passar do último elemento*. Pense no comportamento do método `MoveNext` em um enumerador: ele retorna falso quando a enumeração passa do último elemento. O índice `^0` significa "o fim", `array[array.Length]`, ou o índice que segue o último elemento. Você está familiarizado com `array[2]` significando o elemento "2 desde o início". Agora, `array[^2]` significa o elemento "2 desde o final". 

Você pode especificar um **intervalo** com o **operador de intervalo**: `..`. Por exemplo, `0..^0` especifica todo o intervalo da matriz: 0 desde o início até, mas não incluindo, 0 do final. Qualquer operando pode usar "desde o início" ou "desde o final". Além disso, qualquer operando pode ser omitido. Os padrões são `0` para o índice de início, e `^0` para o índice final.

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

O índice de cada elemento reforça o conceito de "do início" e "do final", e que os intervalos excluem o fim do intervalo. O "início" de toda a matriz é o primeiro elemento. O "final" de toda a matriz ocorre *após* o último elemento.

Você pode recuperar a última palavra com o índice `^1`. Adicione o código a seguir abaixo da inicialização:

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

O código a seguir cria um subintervalo com as palavras "quick", "brown" e "fox". Ele inclui `words[1]` até `words[3]`. O elemento `words[4]` não está no intervalo. Adicione o seguinte código ao mesmo método. Copie e cole-o na parte inferior da janela interativa.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

O código a seguir cria um subintervalo com "lazy" e "dog". Ele inclui `words[^2]` e `words[^1]`. O índice final `words[^0]` não está incluído. Adicione o seguinte código também:

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Os exemplos a seguir criam intervalos abertos para o início, fim ou ambos:

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Você também pode declarar intervalos ou índices como variáveis. A variável então pode ser usada dentro dos caracteres `[` e `]`:

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Os exemplos anteriores mostram duas decisões de design que exigem mais explicação:

- Os intervalos são *exclusivos*, o que significa que o elemento no último índice não está no intervalo.
- O índice `^0` é *o fim* da coleção, não *o último elemento* na coleção.

O exemplo a seguir mostra muitos dos motivos para essas escolhas. Modifique `x`, `y` e `z` para tentar combinações diferentes. Quando você testar, use valores em que `x` é menor que `y` e `y` é menor que `z` para as combinações válidas. Adicione o seguinte código a um novo método. Tente usar combinações diferentes:

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a>Cenários para Intervalos e Índices

Você muitas vezes usará intervalos e índices quando quiser executar uma análise no subintervalo de uma sequência inteira. A nova sintaxe é mais clara para ler exatamente quais subintervalo está envolvido. A função local `MovingAverage` usa um <xref:System.Range> como seu argumento. O método então enumera apenas esse intervalo ao calcular o mínimo, máximo e média. Experimente o seguinte código em seu projeto:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Baixe o código concluído no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes).
