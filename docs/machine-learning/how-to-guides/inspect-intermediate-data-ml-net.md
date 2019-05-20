---
title: Inspecionar valores de dados intermediários durante o processamento do ML.NET
description: Saiba como inspecionar valores de dados intermediários reais durante o processamento de pipeline de aprendizado de máquina do ML.NET
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 06c4a473841db62a10dfc24025f842df7ae2c583
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063512"
---
# <a name="inspect-intermediate-data-values-during-processing"></a>Inspecionar valores de dados intermediários durante o processamento

Saiba como inspecionar os valores de durante as etapas de carregamento, processamento e treinamento do ML.NET.

Dados como aqueles representados abaixo que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView) podem ser inspecionados de várias maneiras no ML.NET.
 
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

Uma das maneiras mais rápidas de inspecionar os valores de uma [`IDataView`](xref:Microsoft.ML.IDataView) é convertê-los em um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601). Para converter um [`IDataView`](xref:Microsoft.ML.IDataView) em [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601), usar o método [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*). 

Para otimizar o desempenho, defina o valor de `reuseRowObject` como `true`. Fazer isso preencherá lentamente o mesmo objeto com os dados da linha atual conforme eles estão sendo avaliados, em vez de criar um novo objeto para cada linha no conjunto de dados.

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

Se você precisar apenas de acesso a uma parte específica dos dados ou índices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) e defina o valor do parâmetro `reuseRowObject` como `false` para que um novo objeto seja criado para cada uma das linhas solicitadas no conjunto de dados. Em seguida, converta a [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) em uma matriz ou lista.

> [!WARNING]
> Converter o resultado de [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) em uma matriz ou lista carregará todas as linhas [`IDataView`](xref:Microsoft.ML.IDataView) solicitados na memória, o que pode afetar o desempenho.

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

Em qualquer ponto no processo de criação de modelo, os valores em uma única coluna de um [`IDataView`](xref:Microsoft.ML.IDataView) podem ser acessados usando o método [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*). O método [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) retorna todos os valores em uma única coluna como um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Inspecione valores IDataView uma linha por vez

[`IDataView`](xref:Microsoft.ML.IDataView) é avaliado lentamente. Para iterar sobre as linhas de uma [`IDataView`](xref:Microsoft.ML.IDataView) sem a conversão em um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) conforme demonstrado nas seções anteriores deste documento, criar um [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) usando o método [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) e passar o [DataViewSchema](xref:Microsoft.ML.DataViewSchema) do seu [`IDataView`](xref:Microsoft.ML.IDataView) como um parâmetro. Em seguida, para iterar sobre linhas, use o método de cursor [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) junto com delegados [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) para extrair os respectivos valores de cada uma das colunas.

> [!IMPORTANT]
> Para fins de desempenho, vetores no ML.NET usam [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601), em vez de tipos de coleção nativos (ou seja, `Vector`,`float[]`). 

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

O processo de criação de modelo é experimental e iterativo. Para visualizar como seria a aparência dos dados após o pré-processamento ou treinar um modelo de machine learning em um subconjunto dos dados, use o método [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) que retorna um [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview). O resultado é um objeto com propriedades `ColumnView` e `RowView` que são ambas um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) e contêm os valores em uma determinada coluna ou linha. Especifique o número de linhas às quais aplicar a transformação com o parâmetro `maxRows`.

![Objeto de visualização do depurador de dados](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

O resultado de inspecionar um [`IDataView`](xref:Microsoft.ML.IDataView) teria uma aparência semelhante à seguinte:

![Exibição de linha de visualização do depurador de dados](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
