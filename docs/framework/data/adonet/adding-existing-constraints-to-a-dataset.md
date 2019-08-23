---
title: Adicionar restrições existentes a um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 05f95a9c4f250100ca97e3ab52e4073d027df1b8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932189"
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="e8738-102">Adicionar restrições existentes a um DataSet</span><span class="sxs-lookup"><span data-stu-id="e8738-102">Adding Existing Constraints to a DataSet</span></span>
<span data-ttu-id="e8738-103">O método **Fill** do **DataAdapter** preenche um <xref:System.Data.DataSet> somente com colunas de tabela e linhas de uma fonte de dados; embora as restrições sejam normalmente definidas pela fonte de dados, o método **Fill** não adiciona essas informações de esquema ao  **DataSet** por padrão.</span><span class="sxs-lookup"><span data-stu-id="e8738-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="e8738-104">Para popular um **conjunto** de dados com informações de restrição de chave primária existentes de uma fonte, você pode chamar o método **FillSchema** do **DataAdapter**ou definir a propriedade **MissingSchemaAction** do **DataAdapter** para **AddWithKey** antes de chamar **Fill**.</span><span class="sxs-lookup"><span data-stu-id="e8738-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="e8738-105">Isso garantirá que as restrições de chave primária no **DataSet** reflitam aquelas na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e8738-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="e8738-106">As informações de restrição de chave estrangeira não estão incluídas e devem ser criadas explicitamente, conforme mostrado em [restrições de DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="e8738-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="e8738-107">A adição de informações de esquema a um **conjunto** de dados antes de preenchê-lo com o data <xref:System.Data.DataTable> garante que as restrições de chave primária sejam incluídas com os objetos no **conjunto**.</span><span class="sxs-lookup"><span data-stu-id="e8738-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="e8738-108">Como resultado, quando são feitas chamadas adicionais para preencher o **conjunto** de dados, as informações da coluna de chave primária são usadas para fazer a correspondência de novas linhas a partir da fonte com as linhas atuais em cada **DataTable**, e os dados atuais nas tabelas são substituídos pelos dados do fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e8738-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="e8738-109">Sem as informações de esquema, as novas linhas da fonte de dados são acrescentadas ao **DataSet**, resultando em linhas duplicadas.</span><span class="sxs-lookup"><span data-stu-id="e8738-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8738-110">Se uma coluna em uma fonte de dados for identificada como incrementação automática, o método **FillSchema** ou o método **Fill** com um **MissingSchemaAction** de **AddWithKey**, criará uma **DataColumn** com uma propriedade AutoIncrement Defina como `true`.</span><span class="sxs-lookup"><span data-stu-id="e8738-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="e8738-111">No entanto, você precisará definir os valores **AutoIncrementStep** e **AutoIncrementSeed** por conta própria.</span><span class="sxs-lookup"><span data-stu-id="e8738-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="e8738-112">Para obter mais informações sobre colunas de incrementação automática, consulte [criando colunas](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)de incremento automático.</span><span class="sxs-lookup"><span data-stu-id="e8738-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
 <span data-ttu-id="e8738-113">O uso de **FillSchema** ou a definição de **MissingSchemaAction** como **AddWithKey** requer processamento extra na fonte de dados para determinar as informações da coluna de chave primária.</span><span class="sxs-lookup"><span data-stu-id="e8738-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="e8738-114">Esse processamento adicional pode impedir o desempenho.</span><span class="sxs-lookup"><span data-stu-id="e8738-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="e8738-115">Se você souber as informações de chave primária em tempo de design, recomendamos especificar explicitamente a coluna de chave primária ou as colunas para obter o desempenho ideal.</span><span class="sxs-lookup"><span data-stu-id="e8738-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="e8738-116">Para obter informações sobre como definir explicitamente informações de chave primária para uma tabela, consulte [definindo chaves primárias](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="e8738-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="e8738-117">O exemplo de código a seguir mostra como adicionar informações de esquema a um **conjunto** de dados usando **FillSchema**.</span><span class="sxs-lookup"><span data-stu-id="e8738-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 <span data-ttu-id="e8738-118">O exemplo de código a seguir mostra como adicionar informações de esquema a um **conjunto** de dados usando a propriedade **MissingSchemaAction. AddWithKey** do método **Fill** .</span><span class="sxs-lookup"><span data-stu-id="e8738-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="e8738-119">Manipulando vários conjuntos de resultados</span><span class="sxs-lookup"><span data-stu-id="e8738-119">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="e8738-120">Se o **DataAdapter** encontrar vários conjuntos de resultados retornados do **SelectCommand**, ele criará várias tabelas no **conjunto**de linhas.</span><span class="sxs-lookup"><span data-stu-id="e8738-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="e8738-121">As tabelas receberão um nome padrão incremental de base zero da **tabela** *N*, começando com a **tabela** em vez de "Table0".</span><span class="sxs-lookup"><span data-stu-id="e8738-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="e8738-122">Se um nome de tabela for passado como um argumento para o método **FillSchema** , as tabelas receberão um nome incremental com base em zero de **TableName** *N*, começando com **TableName** em vez de "TableName0".</span><span class="sxs-lookup"><span data-stu-id="e8738-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8738-123">Se o método **FillSchema** do objeto **OleDbDataAdapter** for chamado para um comando que retorna vários conjuntos de resultados, somente as informações de esquema do primeiro conjunto de resultados serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="e8738-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="e8738-124">Ao retornar informações de esquema para vários conjuntos de resultados usando o **OleDbDataAdapter**, é recomendável que você especifique um **MissingSchemaAction** de **AddWithKey** e obtenha as informações de esquema ao chamar o **preenchimento** forma.</span><span class="sxs-lookup"><span data-stu-id="e8738-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8738-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8738-125">See also</span></span>

- [<span data-ttu-id="e8738-126">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="e8738-126">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- <span data-ttu-id="e8738-127">[DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="e8738-127">[DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>
- <span data-ttu-id="e8738-128">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e8738-128">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="e8738-129">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e8738-129">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
