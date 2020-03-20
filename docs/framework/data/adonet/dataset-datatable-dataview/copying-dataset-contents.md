---
title: Copiando conteúdo do DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: de13e07eb5c19b8beffa724fec4a128c418a4fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151358"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="92855-102">Copiando conteúdo do DataSet</span><span class="sxs-lookup"><span data-stu-id="92855-102">Copying DataSet Contents</span></span>
<span data-ttu-id="92855-103">Você pode criar uma <xref:System.Data.DataSet> cópia de um para que você possa trabalhar com dados sem afetar os dados originais ou trabalhar com um subconjunto dos dados de um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="92855-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="92855-104">Ao copiar um **Conjunto de Dados,** você pode:</span><span class="sxs-lookup"><span data-stu-id="92855-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="92855-105">Crie uma cópia exata do Conjunto de **Dados**, incluindo o esquema, dados, informações do estado de linha e versões de linha.</span><span class="sxs-lookup"><span data-stu-id="92855-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="92855-106">Crie um **Conjunto de Dados** que contenha o esquema de um Conjunto de **Dados**existente, mas apenas linhas que foram modificadas.</span><span class="sxs-lookup"><span data-stu-id="92855-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="92855-107">Você pode retornar todas as linhas que foram modificadas ou especificar um **DataRowState**específico .</span><span class="sxs-lookup"><span data-stu-id="92855-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="92855-108">Para obter mais informações sobre estados de linha, consulte [Estados de linha e versões de linha](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="92855-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="92855-109">Copie apenas o esquema, ou estrutura relacional, do **DataSet,** sem copiar nenhuma linha.</span><span class="sxs-lookup"><span data-stu-id="92855-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="92855-110">As linhas podem ser importadas em um <xref:System.Data.DataTable> existente usando o <xref:System.Data.DataTable.ImportRow%2A>.</span><span class="sxs-lookup"><span data-stu-id="92855-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="92855-111">Para criar uma cópia exata do Conjunto de **Dados** que inclui <xref:System.Data.DataSet.Copy%2A> esquema e dados, use o método do **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="92855-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="92855-112">O exemplo de código a seguir mostra como criar uma cópia exata do Conjunto de **Dados**.</span><span class="sxs-lookup"><span data-stu-id="92855-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="92855-113">Para criar uma cópia de um Conjunto de **Dados** que inclua esquema e apenas os dados <xref:System.Data.DataSet.GetChanges%2A> que representam linhas **adicionadas,** **modificadas**ou **excluídas,** use o método do Conjunto de **Dados**.</span><span class="sxs-lookup"><span data-stu-id="92855-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="92855-114">Você também pode usar **GetChanges** para retornar apenas linhas com um estado de linha especificado, passando um valor **DataRowState** ao chamar **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="92855-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="92855-115">O exemplo de código a seguir mostra como passar um **DataRowState** ao chamar **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="92855-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="92855-116">Para criar uma cópia de um Conjunto de **Dados** <xref:System.Data.DataSet.Clone%2A> que inclua apenas esquema, use o método do **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="92855-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="92855-117">Você também pode adicionar linhas existentes ao **Conjunto de Dados** clonado usando o método **ImportRow** da Tabela de **Dados**.</span><span class="sxs-lookup"><span data-stu-id="92855-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="92855-118">**ImportRow** adiciona dados, informações de estado de linha e versão de linha à tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="92855-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="92855-119">Os valores de coluna são adicionados somente onde o nome da coluna corresponde e o tipo de dados é compatível.</span><span class="sxs-lookup"><span data-stu-id="92855-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="92855-120">O exemplo de código a seguir cria um clone de um **DataSet** e, em seguida, adiciona as linhas do **Conjunto** de Dados original à tabela **Clientes** no clone **DataSet** para clientes onde a coluna **CountryRegion** tem o valor "Alemanha".</span><span class="sxs-lookup"><span data-stu-id="92855-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="92855-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="92855-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="92855-122">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="92855-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="92855-123">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="92855-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
