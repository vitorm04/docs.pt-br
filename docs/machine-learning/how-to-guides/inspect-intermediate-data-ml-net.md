---
title: Inspecionar dados intermediários durante o processamento do ML.NET
description: Saiba como inspecionar os dados intermediários durante as etapas de treinamento de modelo, processamento e carregamento de pipeline de aprendizado de máquina no ML.NET.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 11df1d5caaa7b7974360d863f85afbff18985e47
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977098"
---
# <a name="inspect-intermediate-data-during-processing"></a><span data-ttu-id="30059-103">Inspecionar dados intermediários durante o processamento</span><span class="sxs-lookup"><span data-stu-id="30059-103">Inspect intermediate data during processing</span></span>

<span data-ttu-id="30059-104">Saiba como inspecionar os dados intermediários durante as etapas de treinamento de modelo, processamento e carregamento.</span><span class="sxs-lookup"><span data-stu-id="30059-104">Learn how to inspect intermediate data during loading, processing, and model training steps in ML.NET.</span></span> <span data-ttu-id="30059-105">Dados intermediários são a saída de cada estágio no pipeline de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="30059-105">Intermediate data is the output of each stage in the machine learning pipeline.</span></span>

<span data-ttu-id="30059-106">Dados intermediários como aqueles representados abaixo que são carregados em um [`IDataView`](xref:Microsoft.ML.IDataView) podem ser inspecionados de várias maneiras no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="30059-106">Intermediate data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>

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

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="30059-107">Converter IDataView em IEnumerable</span><span class="sxs-lookup"><span data-stu-id="30059-107">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="30059-108">Uma das maneiras mais rápidas de inspecionar um [`IDataView`](xref:Microsoft.ML.IDataView) é convertê-los em um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="30059-108">One of the quickest ways to inspect an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="30059-109">Para converter um [`IDataView`](xref:Microsoft.ML.IDataView) em [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601), usar o método [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*).</span><span class="sxs-lookup"><span data-stu-id="30059-109">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

<span data-ttu-id="30059-110">Para otimizar o desempenho, defina `reuseRowObject` como `true`.</span><span class="sxs-lookup"><span data-stu-id="30059-110">To optimize performance, set `reuseRowObject` to `true`.</span></span> <span data-ttu-id="30059-111">Fazer isso preencherá lentamente o mesmo objeto com os dados da linha atual conforme eles estão sendo avaliados, em vez de criar um novo objeto para cada linha no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="30059-111">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

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

## <a name="accessing-specific-indices-with-ienumerable"></a><span data-ttu-id="30059-112">Acessando índices específicos com IEnumerable</span><span class="sxs-lookup"><span data-stu-id="30059-112">Accessing specific indices with IEnumerable</span></span>

<span data-ttu-id="30059-113">Se você precisar apenas de acesso a uma parte específica dos dados ou índices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) e defina o valor do parâmetro `reuseRowObject` como `false` para que um novo objeto seja criado para cada uma das linhas solicitadas no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="30059-113">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="30059-114">Em seguida, converta a [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) em uma matriz ou lista.</span><span class="sxs-lookup"><span data-stu-id="30059-114">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="30059-115">Converter o resultado de [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) em uma matriz ou lista carregará todas as linhas [`IDataView`](xref:Microsoft.ML.IDataView) solicitados na memória, o que pode afetar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="30059-115">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="30059-116">Quando a coleção tiver sido criada, você poderá executar operações nos dados.</span><span class="sxs-lookup"><span data-stu-id="30059-116">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="30059-117">O snippet de código a seguir usa as três primeiras linhas no conjunto de dados e calcula o preço médio atual.</span><span class="sxs-lookup"><span data-stu-id="30059-117">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

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

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="30059-118">Inspecionar valores em uma única coluna</span><span class="sxs-lookup"><span data-stu-id="30059-118">Inspect values in a single column</span></span>

<span data-ttu-id="30059-119">Em qualquer ponto no processo de criação de modelo, os valores em uma única coluna de um [`IDataView`](xref:Microsoft.ML.IDataView) podem ser acessados usando o método [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*).</span><span class="sxs-lookup"><span data-stu-id="30059-119">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span> <span data-ttu-id="30059-120">O método [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) retorna todos os valores em uma única coluna como um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="30059-120">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="30059-121">Inspecione valores IDataView uma linha por vez</span><span class="sxs-lookup"><span data-stu-id="30059-121">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="30059-122">[`IDataView`](xref:Microsoft.ML.IDataView) é avaliado lentamente.</span><span class="sxs-lookup"><span data-stu-id="30059-122">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="30059-123">Para iterar sobre as linhas de uma [`IDataView`](xref:Microsoft.ML.IDataView) sem a conversão em um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) conforme demonstrado nas seções anteriores deste documento, criar um [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) usando o método [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) e passar o [DataViewSchema](xref:Microsoft.ML.DataViewSchema) do seu [`IDataView`](xref:Microsoft.ML.IDataView) como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="30059-123">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="30059-124">Em seguida, para iterar sobre linhas, use o método de cursor [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) junto com delegados [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) para extrair os respectivos valores de cada uma das colunas.</span><span class="sxs-lookup"><span data-stu-id="30059-124">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30059-125">Para fins de desempenho, vetores no ML.NET usam [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601), em vez de tipos de coleção nativos (ou seja, `Vector`,`float[]`).</span><span class="sxs-lookup"><span data-stu-id="30059-125">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span>

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="30059-126">Visualização de resultado do pré-processamento ou do treinamento em um subconjunto dos dados</span><span class="sxs-lookup"><span data-stu-id="30059-126">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="30059-127">Não use `Preview` em código de produção porque ele se destina a depuração e pode reduzir o desempenho.</span><span class="sxs-lookup"><span data-stu-id="30059-127">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="30059-128">O processo de criação de modelo é experimental e iterativo.</span><span class="sxs-lookup"><span data-stu-id="30059-128">The model building process is experimental and iterative.</span></span> <span data-ttu-id="30059-129">Para visualizar como seria a aparência dos dados após o pré-processamento ou treinar um modelo de machine learning em um subconjunto dos dados, use o método [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) que retorna um [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span><span class="sxs-lookup"><span data-stu-id="30059-129">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="30059-130">O resultado é um objeto com propriedades `ColumnView` e `RowView` que são ambas um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) e contêm os valores em uma determinada coluna ou linha.</span><span class="sxs-lookup"><span data-stu-id="30059-130">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="30059-131">Especifique o número de linhas às quais aplicar a transformação com o parâmetro `maxRows`.</span><span class="sxs-lookup"><span data-stu-id="30059-131">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![Objeto de visualização do depurador de dados](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="30059-133">O resultado de inspecionar um [`IDataView`](xref:Microsoft.ML.IDataView) teria uma aparência semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="30059-133">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![Exibição de linha de visualização do depurador de dados](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
