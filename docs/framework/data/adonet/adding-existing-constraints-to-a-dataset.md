---
title: Adicionar restrições existentes a um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 267d6489d39f86fc06b35de8cf30dad74f501b0b
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523242"
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="8ef4e-102">Adicionar restrições existentes a um DataSet</span><span class="sxs-lookup"><span data-stu-id="8ef4e-102">Adding Existing Constraints to a DataSet</span></span>

<span data-ttu-id="8ef4e-103">O método **Fill** do **DataAdapter** preenche uma <xref:System.Data.DataSet> somente com colunas e linhas de tabela de uma fonte de dados; Embora as restrições sejam normalmente definidas pela fonte de dados, o método **Fill** não adiciona essas informações de esquema ao **DataSet** por padrão.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="8ef4e-104">Para popular um **conjunto** de dados com informações de restrição de chave primária existentes de uma fonte, você pode chamar o método **FillSchema** do **DataAdapter**ou definir a propriedade **MissingSchemaAction** do **DataAdapter** para **AddWithKey** antes de chamar **Fill**.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="8ef4e-105">Isso garantirá que as restrições de chave primária no **DataSet** reflitam aquelas na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="8ef4e-106">As informações de restrição de chave estrangeira não estão incluídas e devem ser criadas explicitamente, conforme mostrado em [restrições de DataTable](./dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="8ef4e-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](./dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
<span data-ttu-id="8ef4e-107">A adição de informações de esquema a um **conjunto** de dados antes de preenchê-lo com o data garante que as restrições de chave primária sejam incluídas com os objetos de <xref:System.Data.DataTable> no **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="8ef4e-108">Como resultado, quando são feitas chamadas adicionais para preencher o **conjunto** de dados, as informações da coluna de chave primária são usadas para fazer a correspondência de novas linhas a partir da fonte com as linhas atuais em cada **DataTable**, e os dados atuais nas tabelas são substituídos pelos dados do fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="8ef4e-109">Sem as informações de esquema, as novas linhas da fonte de dados são acrescentadas ao **DataSet**, resultando em linhas duplicadas.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ef4e-110">Se uma coluna em uma fonte de dados for identificada como incrementação automática, o método **FillSchema** ou o método **Fill** com um **MissingSchemaAction** de **AddWithKey**, criará uma **DataColumn** com uma propriedade **AutoIncrement** Defina como `true`.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="8ef4e-111">No entanto, você precisará definir os valores **AutoIncrementStep** e **AutoIncrementSeed** por conta própria.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="8ef4e-112">Para obter mais informações sobre colunas de incrementação automática, consulte [criando colunas de incremento](./dataset-datatable-dataview/creating-autoincrement-columns.md)automático.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](./dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
<span data-ttu-id="8ef4e-113">O uso de **FillSchema** ou a definição de **MissingSchemaAction** como **AddWithKey** requer processamento extra na fonte de dados para determinar as informações da coluna de chave primária.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="8ef4e-114">Esse processamento adicional pode impedir o desempenho.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="8ef4e-115">Se você souber as informações de chave primária em tempo de design, recomendamos especificar explicitamente a coluna de chave primária ou as colunas para obter o desempenho ideal.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="8ef4e-116">Para obter informações sobre como definir explicitamente informações de chave primária para uma tabela, consulte [definindo chaves primárias](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="8ef4e-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>
  
<span data-ttu-id="8ef4e-117">O exemplo de código a seguir mostra como adicionar informações de esquema a um **conjunto** de dados usando **FillSchema**:</span><span class="sxs-lookup"><span data-stu-id="8ef4e-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**:</span></span>
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
<span data-ttu-id="8ef4e-118">O exemplo de código a seguir mostra como adicionar informações de esquema a um **conjunto** de dados usando a propriedade **MissingSchemaAction. AddWithKey** do método **Fill** :</span><span class="sxs-lookup"><span data-stu-id="8ef4e-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method:</span></span>
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="8ef4e-119">Manipulando vários conjuntos de resultados</span><span class="sxs-lookup"><span data-stu-id="8ef4e-119">Handling multiple result sets</span></span>  

<span data-ttu-id="8ef4e-120">Se o **DataAdapter** encontrar vários conjuntos de resultados retornados do **SelectCommand**, ele criará várias tabelas no **conjunto**de linhas.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="8ef4e-121">As tabelas receberão um nome padrão incremental de base zero da **tabela** *N*, começando com a **tabela** em vez de "Table0".</span><span class="sxs-lookup"><span data-stu-id="8ef4e-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="8ef4e-122">Se um nome de tabela for passado como um argumento para o método **FillSchema** , as tabelas receberão um nome incremental com base em zero de **TableName** *N*, começando com **TableName** em vez de "TableName0".</span><span class="sxs-lookup"><span data-stu-id="8ef4e-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ef4e-123">Se o método **FillSchema** do objeto **OleDbDataAdapter** for chamado para um comando que retorna vários conjuntos de resultados, somente as informações de esquema do primeiro conjunto de resultados serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="8ef4e-124">Ao retornar informações de esquema para vários conjuntos de resultados usando o **OleDbDataAdapter**, é recomendável que você especifique um **MissingSchemaAction** de **AddWithKey** e obtenha as informações de esquema ao chamar o **preenchimento** forma.</span><span class="sxs-lookup"><span data-stu-id="8ef4e-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef4e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ef4e-125">See also</span></span>

- [<span data-ttu-id="8ef4e-126">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="8ef4e-126">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- <span data-ttu-id="8ef4e-127">[DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="8ef4e-127">[DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md)</span></span>
- <span data-ttu-id="8ef4e-128">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8ef4e-128">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="8ef4e-129">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8ef4e-129">[ADO.NET Overview](ado-net-overview.md)</span></span>
