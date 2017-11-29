---
title: Exibindo dados em uma DataTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 147d6fb4509913de1f0331ce2ff6c580c6e41ef3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="3a70a-102">Exibindo dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="3a70a-102">Viewing Data in a DataTable</span></span>
<span data-ttu-id="3a70a-103">Você pode acessar o conteúdo de um <xref:System.Data.DataTable> usando o **linhas** e **colunas** coleções do **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="3a70a-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="3a70a-104">Você também pode usar o <xref:System.Data.DataTable.Select%2A> método para retornar subconjuntos de dados em um **DataTable** acordo com critérios inclusive critérios de pesquisa, ordem de classificação e o estado de linha.</span><span class="sxs-lookup"><span data-stu-id="3a70a-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="3a70a-105">Além disso, você pode usar o <xref:System.Data.DataRowCollection.Find%2A> método o **DataRowCollection** durante a pesquisa de uma linha específica usando um valor de chave primária.</span><span class="sxs-lookup"><span data-stu-id="3a70a-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>  
  
 <span data-ttu-id="3a70a-106">O **selecione** método o **DataTable** objeto retorna um conjunto de <xref:System.Data.DataRow> objetos que correspondem aos critérios especificados.</span><span class="sxs-lookup"><span data-stu-id="3a70a-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="3a70a-107">**Selecione** leva argumentos opcionais de uma expressão de filtro, a expressão de classificação, e **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="3a70a-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="3a70a-108">A expressão de filtro identifica quais linhas a serem retornadas com base em **DataColumn** valores, como `LastName = 'Smith'`.</span><span class="sxs-lookup"><span data-stu-id="3a70a-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="3a70a-109">A expressão de classificação segue as convenções padrão de SQL para ordenar colunas, por exemplo `LastName ASC, FirstName ASC`.</span><span class="sxs-lookup"><span data-stu-id="3a70a-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="3a70a-110">Para obter regras sobre como escrever expressões, consulte o <xref:System.Data.DataColumn.Expression%2A> propriedade o **DataColumn** classe.</span><span class="sxs-lookup"><span data-stu-id="3a70a-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="3a70a-111">Se você estiver executando um número de chamadas para o **selecione** método de um **DataTable**, você pode aumentar o desempenho criando primeiro uma <xref:System.Data.DataView> para o **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="3a70a-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="3a70a-112">Criando o **DataView** indexa as linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="3a70a-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="3a70a-113">O **selecione** método e usará o índice, reduzindo significativamente o tempo para gerar o resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="3a70a-113">The **Select** method then usees that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="3a70a-114">Para obter informações sobre como criar um **DataView** para um **DataTable**, consulte [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span><span class="sxs-lookup"><span data-stu-id="3a70a-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span></span>  
  
 <span data-ttu-id="3a70a-115">O **selecione** método determina qual versão das linhas para exibir ou manipular com base em um <xref:System.Data.DataViewRowState>.</span><span class="sxs-lookup"><span data-stu-id="3a70a-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="3a70a-116">A tabela a seguir descreve os possíveis **DataViewRowState** valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="3a70a-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>  
  
|<span data-ttu-id="3a70a-117">Valor de DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="3a70a-117">DataViewRowState value</span></span>|<span data-ttu-id="3a70a-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a70a-118">Description</span></span>|  
|----------------------------|-----------------|  
|<span data-ttu-id="3a70a-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="3a70a-119">**CurrentRows**</span></span>|<span data-ttu-id="3a70a-120">Linhas atuais, incluindo inalteradas, adicionadas e modificadas.</span><span class="sxs-lookup"><span data-stu-id="3a70a-120">Current rows including unchanged, added, and modified rows.</span></span>|  
|<span data-ttu-id="3a70a-121">**Excluído**</span><span class="sxs-lookup"><span data-stu-id="3a70a-121">**Deleted**</span></span>|<span data-ttu-id="3a70a-122">Uma linha excluída.</span><span class="sxs-lookup"><span data-stu-id="3a70a-122">A deleted row.</span></span>|  
|<span data-ttu-id="3a70a-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="3a70a-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="3a70a-124">A versão atual, que é uma versão modificada dos dados originais.</span><span class="sxs-lookup"><span data-stu-id="3a70a-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="3a70a-125">(Consulte **ModifiedOriginal**.)</span><span class="sxs-lookup"><span data-stu-id="3a70a-125">(See **ModifiedOriginal**.)</span></span>|  
|<span data-ttu-id="3a70a-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="3a70a-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="3a70a-127">A versão original de todas as linhas alteradas.</span><span class="sxs-lookup"><span data-stu-id="3a70a-127">The original version of all modified rows.</span></span> <span data-ttu-id="3a70a-128">A versão atual está disponível com **ModifiedCurrent**.</span><span class="sxs-lookup"><span data-stu-id="3a70a-128">The current version is available using **ModifiedCurrent**.</span></span>|  
|<span data-ttu-id="3a70a-129">**Adicionado**</span><span class="sxs-lookup"><span data-stu-id="3a70a-129">**Added**</span></span>|<span data-ttu-id="3a70a-130">Uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="3a70a-130">A new row.</span></span>|  
|<span data-ttu-id="3a70a-131">**Nenhum**</span><span class="sxs-lookup"><span data-stu-id="3a70a-131">**None**</span></span>|<span data-ttu-id="3a70a-132">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3a70a-132">None.</span></span>|  
|<span data-ttu-id="3a70a-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="3a70a-133">**OriginalRows**</span></span>|<span data-ttu-id="3a70a-134">Linhas originais, incluindo linhas inalteradas e excluídas.</span><span class="sxs-lookup"><span data-stu-id="3a70a-134">Original rows, including unchanged and deleted rows.</span></span>|  
|<span data-ttu-id="3a70a-135">**Inalterado**</span><span class="sxs-lookup"><span data-stu-id="3a70a-135">**Unchanged**</span></span>|<span data-ttu-id="3a70a-136">Uma linha inalterada.</span><span class="sxs-lookup"><span data-stu-id="3a70a-136">An unchanged row.</span></span>|  
  
 <span data-ttu-id="3a70a-137">No exemplo a seguir, o **DataSet** objeto for filtrado para que você está apenas trabalhando com linhas cuja **DataViewRowState** é definido como **CurrentRows**.</span><span class="sxs-lookup"><span data-stu-id="3a70a-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 <span data-ttu-id="3a70a-138">O **selecione** método pode ser usado para retornar linhas com diferentes **RowState** valores ou valores de campo.</span><span class="sxs-lookup"><span data-stu-id="3a70a-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="3a70a-139">O exemplo a seguir retorna um **DataRow** matriz que faz referência a todas as linhas que foram excluídas e retorna outro **DataRow** matriz que faz referência a todas as linhas, ordenados por **CustLName**, onde o **CustID** coluna é maior que 5.</span><span class="sxs-lookup"><span data-stu-id="3a70a-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="3a70a-140">Para obter informações sobre como exibir as informações de **excluído** de linha, consulte [estados de linha e versões de linha](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="3a70a-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a70a-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a70a-141">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [<span data-ttu-id="3a70a-142">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="3a70a-142">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="3a70a-143">Estados de linha e versões de linha</span><span class="sxs-lookup"><span data-stu-id="3a70a-143">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 <span data-ttu-id="3a70a-144">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3a70a-144">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
