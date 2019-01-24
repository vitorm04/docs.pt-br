---
title: Estados de linha e versões de linha
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 38166addf95679083932a4369d19b75421a64665
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559574"
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="ce9c8-102">Estados de linha e versões de linha</span><span class="sxs-lookup"><span data-stu-id="ce9c8-102">Row States and Row Versions</span></span>
<span data-ttu-id="ce9c8-103">O ADO.NET gerencia linhas nas tabelas usando estados de linha e versões.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="ce9c8-104">Um estado de linha indica o status de uma linha; as versões de linha mantêm os valores armazenados em uma linha à medida que são modificados, incluindo os valores atuais, originais e padrão.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="ce9c8-105">Por exemplo, depois que você tiver feito uma alteração em uma coluna em uma linha, a linha terá um estado de linha de `Modified` e duas versões de linha: `Current`, que contém os valores atuais de linha e `Original`, que contém os valores de linha antes que a coluna foi modificada.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="ce9c8-106">Cada objeto <xref:System.Data.DataRow> tem uma propriedade <xref:System.Data.DataRow.RowState%2A> que você pode examinar para determinar o estado atual da linha.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="ce9c8-107">A tabela a seguir dá a você uma breve descrição de cada valor de enumeração `RowState`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="ce9c8-108">Valor de RowState</span><span class="sxs-lookup"><span data-stu-id="ce9c8-108">RowState value</span></span>|<span data-ttu-id="ce9c8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce9c8-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="ce9c8-110">Nenhuma alteração foi feita desde a última chamada para `AcceptChanges` ou desde que a linha foi criada por `DataAdapter.Fill`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="ce9c8-111">A linha foi adicionada à tabela, mas `AcceptChanges` não foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="ce9c8-112">Algum elemento da linha foi alterado.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="ce9c8-113">A linha foi excluída da tabela e `AcceptChanges` não foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="ce9c8-114">A linha não faz parte de nenhum `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="ce9c8-115">O `RowState` de uma linha recém-criada é definido como `Detached`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="ce9c8-116">Após o novo `DataRow` ser adicionado ao `DataRowCollection` chamando o método `Add`, o valor da propriedade `RowState` é definido como `Added`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="ce9c8-117">`Detached` também são definidos para uma linha que foi removida de um `DataRowCollection` usando o método `Remove` ou o método `Delete` seguido pelo método `AcceptChanges`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="ce9c8-118">Quando `AcceptChanges` tiver sido chamado em um <xref:System.Data.DataSet>, <xref:System.Data.DataTable> ou <xref:System.Data.DataRow>, todas as linhas com um estado de linha de `Deleted` serão removidas.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="ce9c8-119">As linhas restantes recebem um estado de linha de `Unchanged` e os valores na versão de linha `Original` são substituídos pelos valores da versão de linha `Current`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="ce9c8-120">Quando `RejectChanges` tiver sido chamado, todas as linhas com um estado de `Added` serão removidas.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="ce9c8-121">As linhas restantes recebem um estado de linha de `Unchanged` e os valores na versão de linha `Current` são substituídos pelos valores da versão de linha `Original`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="ce9c8-122">Você pode exibir as versões de linha diferentes de uma linha passando um parâmetro <xref:System.Data.DataRowVersion> com a referência de coluna, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="ce9c8-123">A tabela a seguir dá a você uma breve descrição de cada valor de enumeração `DataRowVersion`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="ce9c8-124">Valor de DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="ce9c8-124">DataRowVersion value</span></span>|<span data-ttu-id="ce9c8-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce9c8-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="ce9c8-126">Os valores atuais para a linha.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-126">The current values for the row.</span></span> <span data-ttu-id="ce9c8-127">Esta versão de linha não existe para linhas com um `RowState` de `Deleted`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="ce9c8-128">A versão de linha padrão para uma linha específica.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-128">The default row version for a particular row.</span></span> <span data-ttu-id="ce9c8-129">A versão de linha padrão para uma linha `Added`, `Modified` ou `Deleted` é `Current`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-129">The default row version for an `Added`, `Modified`, or `Deleted` row is `Current`.</span></span> <span data-ttu-id="ce9c8-130">A versão de linha padrão para uma linha `Detached` é `Proposed`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-130">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="ce9c8-131">Os valores originais para a linha.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-131">The original values for the row.</span></span> <span data-ttu-id="ce9c8-132">Esta versão de linha não existe para linhas com um `RowState` de `Added`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-132">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="ce9c8-133">Os valores propostos para a linha.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-133">The proposed values for the row.</span></span> <span data-ttu-id="ce9c8-134">Esta versão de linha existe durante uma operação de edição em uma linha ou para uma linha que não faz parte de um `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-134">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="ce9c8-135">Você pode testar se um `DataRow` tem uma versão de linha específica chamando o método <xref:System.Data.DataRow.HasVersion%2A> e passando `DataRowVersion` como argumento.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-135">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="ce9c8-136">Por exemplo, `DataRow.HasVersion(DataRowVersion.Original)` retornará `false` para linhas recém-adicionadas antes que `AcceptChanges` tenha sido chamado.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-136">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="ce9c8-137">O exemplo de código a seguir exibe os valores em todas as linhas excluídas de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-137">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="ce9c8-138">As linhas `Deleted` não têm uma versão de linha `Current`; portanto, você deve passar `DataRowVersion.Original` ao acessar os valores de coluna.</span><span class="sxs-lookup"><span data-stu-id="ce9c8-138">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce9c8-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce9c8-139">See also</span></span>
- [<span data-ttu-id="ce9c8-140">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="ce9c8-140">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- <span data-ttu-id="ce9c8-141">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="ce9c8-141">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>
- [<span data-ttu-id="ce9c8-142">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="ce9c8-142">DataAdapters and DataReaders</span></span>](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- <span data-ttu-id="ce9c8-143">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ce9c8-143">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
