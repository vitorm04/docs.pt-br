---
title: "Copiando conteúdo do DataSet"
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
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d8f9eac80d7a6679e7b3717446e79caf54a5fed3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="d4188-102">Copiando conteúdo do DataSet</span><span class="sxs-lookup"><span data-stu-id="d4188-102">Copying DataSet Contents</span></span>
<span data-ttu-id="d4188-103">Você pode criar uma cópia de um <xref:System.Data.DataSet> para que você possa trabalhar com dados sem afetar os dados originais ou trabalhar com um subconjunto dos dados de um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="d4188-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="d4188-104">Ao copiar um **conjunto de dados**, você pode:</span><span class="sxs-lookup"><span data-stu-id="d4188-104">When copying a **DataSet**, you can:</span></span>  
  
-   <span data-ttu-id="d4188-105">Criar uma cópia exata do **conjunto de dados**, incluindo o esquema, dados, informações de estado de linha e versões de linha.</span><span class="sxs-lookup"><span data-stu-id="d4188-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
-   <span data-ttu-id="d4188-106">Criar um **DataSet** que contém o esquema de um objeto existente **conjunto de dados**, mas somente as linhas que foram modificadas.</span><span class="sxs-lookup"><span data-stu-id="d4188-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="d4188-107">Você pode retornar todas as linhas que foram modificadas, ou especificar um determinado **DataRowState**.</span><span class="sxs-lookup"><span data-stu-id="d4188-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="d4188-108">Para obter mais informações sobre estados de linha, consulte [estados de linha e versões de linha](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="d4188-108">For more information about row states, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
-   <span data-ttu-id="d4188-109">Copie o esquema, ou estrutura relacional, do **DataSet** somente, sem copiar linhas.</span><span class="sxs-lookup"><span data-stu-id="d4188-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="d4188-110">As linhas podem ser importadas em um <xref:System.Data.DataTable> existente usando o <xref:System.Data.DataTable.ImportRow%2A>.</span><span class="sxs-lookup"><span data-stu-id="d4188-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="d4188-111">Para criar uma cópia exata do **DataSet** que inclui o esquema e os dados, use o <xref:System.Data.DataSet.Copy%2A> método o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="d4188-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="d4188-112">O exemplo de código a seguir mostra como criar uma cópia exata do **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="d4188-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="d4188-113">Para criar uma cópia de um **DataSet** que inclui o esquema e apenas os dados que representa **adicionado**, **modificadas**, ou **excluído** linhas, use o <xref:System.Data.DataSet.GetChanges%2A> método o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="d4188-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="d4188-114">Você também pode usar **GetChanges** para retornar apenas as linhas com um estado de linha especificada, passando um **DataRowState** valor ao chamar **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="d4188-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="d4188-115">O exemplo de código a seguir mostra como passar um **DataRowState** ao chamar **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="d4188-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 <span data-ttu-id="d4188-116">Para criar uma cópia de um **conjunto de dados** que inclui somente esquema, use o <xref:System.Data.DataSet.Clone%2A> método o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="d4188-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="d4188-117">Você também pode adicionar linhas existentes para o clonado **DataSet** usando o **ImportRow** método o **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="d4188-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="d4188-118">**ImportRow** adiciona dados, o estado de linha e informações de versão de linha à tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="d4188-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="d4188-119">Os valores de coluna são adicionados somente onde o nome da coluna corresponde e o tipo de dados é compatível.</span><span class="sxs-lookup"><span data-stu-id="d4188-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="d4188-120">O exemplo de código a seguir cria um clone de um **DataSet** e, em seguida, adiciona as linhas do original **DataSet** para o **clientes** tabela o **conjunto de dados**  clone para clientes onde o **CountryRegion** coluna tem o valor "Germany".</span><span class="sxs-lookup"><span data-stu-id="d4188-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4188-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4188-121">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="d4188-122">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="d4188-122">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="d4188-123">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d4188-123">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
