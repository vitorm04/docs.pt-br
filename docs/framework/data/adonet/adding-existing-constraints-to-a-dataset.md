---
title: Adicionar restrições existentes a um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 18c391e97baa170b78dcfe0165fb38b6c6d739f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210549"
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="8731b-102">Adicionar restrições existentes a um DataSet</span><span class="sxs-lookup"><span data-stu-id="8731b-102">Adding Existing Constraints to a DataSet</span></span>
<span data-ttu-id="8731b-103">O **preencher** método o **DataAdapter** preenche um <xref:System.Data.DataSet> somente com colunas de tabelas e linhas de uma fonte de dados; no entanto as restrições são geralmente definidas pela fonte de dados, o **preencher** método não adiciona essas informações de esquema para o **conjunto de dados** por padrão.</span><span class="sxs-lookup"><span data-stu-id="8731b-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="8731b-104">Para preencher uma **DataSet** com informações de restrição de chave primária existente de uma fonte de dados, você pode chamar o **FillSchema** método da **DataAdapter**, ou defina o **MissingSchemaAction** propriedade da **DataAdapter** para **AddWithKey** antes de chamar **preencher**.</span><span class="sxs-lookup"><span data-stu-id="8731b-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="8731b-105">Isso garantirá que a chave primária restrições na **conjunto de dados** refletem as na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8731b-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="8731b-106">Informações de restrição de chave estrangeira não está incluídas e devem ser criadas explicitamente, conforme mostrado na [restrições de DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="8731b-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="8731b-107">Adicionando informações de esquema para um **DataSet** antes de preenchê-lo com dados garante que as restrições de chave primária são incluídas com o <xref:System.Data.DataTable> objetos no **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="8731b-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="8731b-108">Como resultado, quando adicionais chamadas para preencher a **conjunto de dados** forem feitas, o primário informações de coluna de chave são usadas para corresponder as novas linhas da fonte de dados com linhas atuais em cada **DataTable**e os dados atuais as tabelas serão substituídas pelos dados da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8731b-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="8731b-109">Sem as informações de esquema, as novas linhas da fonte de dados são acrescentadas à **conjunto de dados**, resultando em linhas duplicadas.</span><span class="sxs-lookup"><span data-stu-id="8731b-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8731b-110">Se uma coluna em uma fonte de dados for identificada como incremento automático, o **FillSchema** método, ou o **preencher** método com um **MissingSchemaAction** de  **AddWithKey**, cria um **DataColumn** com um **AutoIncrement** propriedade definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="8731b-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="8731b-111">No entanto, você precisará definir a **AutoIncrementStep** e **AutoIncrementSeed** valores por conta própria.</span><span class="sxs-lookup"><span data-stu-id="8731b-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="8731b-112">Para obter mais informações sobre colunas de incremento automático, consulte [criando colunas de incremento automático](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span><span class="sxs-lookup"><span data-stu-id="8731b-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
 <span data-ttu-id="8731b-113">Usando o **FillSchema** configuração ou o **MissingSchemaAction** para **AddWithKey** exige processamento extra na fonte de dados para determinar as informações de coluna de chave primária.</span><span class="sxs-lookup"><span data-stu-id="8731b-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="8731b-114">Esse processamento adicional pode prejudicar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="8731b-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="8731b-115">Se você souber que as informações de chave primárias em tempo de design, é recomendável que você especifique explicitamente a coluna de chave primária ou colunas para alcançar um desempenho ideal.</span><span class="sxs-lookup"><span data-stu-id="8731b-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="8731b-116">Para obter informações sobre como definir explicitamente as informações de chave primária para uma tabela, consulte [definindo chaves primárias](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="8731b-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="8731b-117">O exemplo de código a seguir mostra como adicionar informações de esquema para um **DataSet** usando **FillSchema**.</span><span class="sxs-lookup"><span data-stu-id="8731b-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**.</span></span>  
  
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
  
 <span data-ttu-id="8731b-118">O exemplo de código a seguir mostra como adicionar informações de esquema para um **DataSet** usando o **MissingSchemaAction.AddWithKey** propriedade do **preencher** método.</span><span class="sxs-lookup"><span data-stu-id="8731b-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method.</span></span>  
  
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
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="8731b-119">Manipulando vários conjuntos de resultados</span><span class="sxs-lookup"><span data-stu-id="8731b-119">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="8731b-120">Se o **DataAdapter** encontra vários conjuntos de resultados retornados da **SelectCommand**, ele criará várias tabelas no **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="8731b-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="8731b-121">As tabelas terá um nome padrão incremental com base em zero da **tabela** *N*, começando com **tabela** em vez de "Table0".</span><span class="sxs-lookup"><span data-stu-id="8731b-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="8731b-122">Se um nome de tabela é passado como um argumento para o **FillSchema** método, as tabelas terá um nome incremental com base em zero da **TableName** *N*, começando com **TableName** em vez de "TableName0".</span><span class="sxs-lookup"><span data-stu-id="8731b-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8731b-123">Se o **FillSchema** método o **OleDbDataAdapter** objeto é chamado para um comando que retorna vários conjuntos de resultados, somente as informações de esquema do primeiro conjunto de resultados serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="8731b-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="8731b-124">Quando, retornando informações de esquema de resultados múltiplos conjuntos usando o **OleDbDataAdapter**, é recomendável que você especifique uma **MissingSchemaAction** dos **AddWithKey** e obter as informações de esquema ao chamar o **preencher** método.</span><span class="sxs-lookup"><span data-stu-id="8731b-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8731b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8731b-125">See also</span></span>

- [<span data-ttu-id="8731b-126">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="8731b-126">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="8731b-127">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="8731b-127">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="8731b-128">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8731b-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="8731b-129">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="8731b-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
