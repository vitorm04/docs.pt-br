---
title: Inspecionar dados intermediários durante o processamento do ML.NET
description: Saiba como inspecionar os dados intermediários durante as etapas de treinamento de modelo, processamento e carregamento de pipeline de aprendizado de máquina no ML.NET.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 11df1d5caaa7b7974360d863f85afbff18985e47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977098"
---
# <a name="inspect-intermediate-data-during-processing"></a>Inspecionar dados intermediários durante o processamento

Saiba como inspecionar os dados intermediários durante as etapas de treinamento de modelo, processamento e carregamento. Dados intermediários são a saída de cada estágio no pipeline de aprendizado de máquina.

Dados intermediários como o representado abaixo, [`IDataView`](xref:Microsoft.ML.IDataView) que é carregado em um, podem ser inspecionados de várias maneiras em ML.NET.

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

## <a name="convert-idataview-to-ienumerable"></a>Converter IDataView em IEnumerable

Uma das maneiras mais [`IDataView`](xref:Microsoft.ML.IDataView) rápidas de inspecionar [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)um é convertê-lo em um . Para converter [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) um [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) para usar o método.

Para otimizar o desempenho, defina `reuseRowObject` como `true`. Fazer isso preencherá lentamente o mesmo objeto com os dados da linha atual conforme eles estão sendo avaliados, em vez de criar um novo objeto para cada linha no conjunto de dados.

```csharp
// Create an IEnumerable of HousingData objects from IDataView
IEnumerable<HousingData> housingDataEnumerable =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: true);

// Iterate over each row
foreach (HousingData row in housingDataEnumerable)
{
    // Do something (print out Size property) with current Housing Data object being evaluated
    Console.WriteLine(row.Size);
}
```

## <a name="accessing-specific-indices-with-ienumerable"></a>Acessando índices específicos com IEnumerable

Se você precisar apenas acessar uma parte dos dados [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) ou `reuseRowObject` índices específicos, use e defina o valor do parâmetro para `false` que um novo objeto seja criado para cada uma das linhas solicitadas no conjunto de dados. Em seguida, [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) converta o em uma matriz ou lista.

> [!WARNING]
> A conversão do [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) resultado em uma matriz ou [`IDataView`](xref:Microsoft.ML.IDataView) lista carregará todas as linhas solicitadas na memória, o que pode afetar o desempenho.

Quando a coleção tiver sido criada, você poderá executar operações nos dados. O snippet de código a seguir usa as três primeiras linhas no conjunto de dados e calcula o preço médio atual.

```csharp
// Create an Array of HousingData objects from IDataView
HousingData[] housingDataArray =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: false)
        .Take(3)
        .ToArray();

// Calculate Average CurrentPrice of First Three Elements
HousingData firstRow = housingDataArray[0];
HousingData secondRow = housingDataArray[1];
HousingData thirdRow = housingDataArray[2];
float averageCurrentPrice = (firstRow.CurrentPrice + secondRow.CurrentPrice + thirdRow.CurrentPrice) / 3;
```

## <a name="inspect-values-in-a-single-column"></a>Inspecionar valores em uma única coluna

Em qualquer ponto do processo de construção do [`IDataView`](xref:Microsoft.ML.IDataView) modelo, valores [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) em uma única coluna de um podem ser acessados usando o método. O [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) método retorna todos os valores [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)em uma única coluna como um .

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Inspecione valores IDataView uma linha por vez

[`IDataView`](xref:Microsoft.ML.IDataView)é preguiçosamente avaliado. Para iterar sobre as [`IDataView`](xref:Microsoft.ML.IDataView) linhas de um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) sem converter para um como [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) demonstrado em [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) seções anteriores deste documento, [`IDataView`](xref:Microsoft.ML.IDataView) crie um usando o método e passando no [DataViewSchema](xref:Microsoft.ML.DataViewSchema) do seu como parâmetro. Em seguida, para iterar sobre [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) linhas, use [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) o método do cursor junto com os delegados para extrair os respectivos valores de cada uma das colunas.

> [!IMPORTANT]
> Para fins de desempenho, [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) os vetores em ML.NET `Vector`usam`float[]`em vez de tipos nativos de coleta (isto é, ).

```csharp
// Get DataViewSchema of IDataView
DataViewSchema columns = data.Schema;

// Create DataViewCursor
using (DataViewRowCursor cursor = data.GetRowCursor(columns))
{
    // Define variables where extracted values will be stored to
    float size = default;
    VBuffer<float> historicalPrices = default;
    float currentPrice = default;

    // Define delegates for extracting values from columns
    ValueGetter<float> sizeDelegate = cursor.GetGetter<float>(columns[0]);
    ValueGetter<VBuffer<float>> historicalPriceDelegate = cursor.GetGetter<VBuffer<float>>(columns[1]);
    ValueGetter<float> currentPriceDelegate = cursor.GetGetter<float>(columns[2]);

    // Iterate over each row
    while (cursor.MoveNext())
    {
        //Get values from respective columns
        sizeDelegate.Invoke(ref size);
        historicalPriceDelegate.Invoke(ref historicalPrices);
        currentPriceDelegate.Invoke(ref currentPrice);
    }
}
```

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a>Visualização de resultado do pré-processamento ou do treinamento em um subconjunto dos dados

> [!WARNING]
> Não use `Preview` em código de produção porque ele se destina a depuração e pode reduzir o desempenho.

O processo de criação de modelo é experimental e iterativo. Para visualizar como seriam os dados após o pré-processamento ou treinamento de um [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) modelo de [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview)aprendizado de máquina em um subconjunto de dados, use o método que retorna a . O resultado é `ColumnView` um `RowView` objeto com [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) e propriedades que são tanto um e contêm os valores em uma determinada coluna ou linha. Especifique o número de linhas às quais aplicar a transformação com o parâmetro `maxRows`.

![Objeto de visualização do depurador de dados](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

O resultado da [`IDataView`](xref:Microsoft.ML.IDataView) inspeção de um seria semelhante ao seguinte:

![Exibição de linha de visualização do depurador de dados](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
