---
title: Mapeamentos de DataTable e de DataColumn do DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6aaaa126a0b19300abc2c10b88b0e4ff39a3ad66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530423"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="c7fd2-102">Mapeamentos de DataTable e de DataColumn do DataAdapter</span><span class="sxs-lookup"><span data-stu-id="c7fd2-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="c7fd2-103">Um **DataAdapter** contém uma coleção de zero ou mais <xref:System.Data.Common.DataTableMapping> objetos no seu **TableMappings** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="c7fd2-104">Um **DataTableMapping** fornece um mapeamento mestre entre os dados retornados de uma consulta em relação a uma fonte de dados e um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="c7fd2-105">O **DataTableMapping** nome pode ser passado em vez da **DataTable** nome para o **preencher** o método da **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="c7fd2-106">O exemplo a seguir cria uma **DataTableMapping** denominado **AuthorsMapping** para o **autores** tabela.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="c7fd2-107">Um **DataTableMapping** permite que você use nomes de coluna em uma **DataTable** que são diferentes no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="c7fd2-108">O **DataAdapter** usa o mapeamento para corresponder às colunas quando a tabela é atualizada.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="c7fd2-109">Se você não especificar uma **TableName** ou um **DataTableMapping** nome ao chamar o **preencher** ou **atualização** método o  **DataAdapter**, o **DataAdapter** procura uma **DataTableMapping** chamado "Table".</span><span class="sxs-lookup"><span data-stu-id="c7fd2-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="c7fd2-110">Se esse **DataTableMapping** não existir, o **TableName** dos **DataTable** será "Table".</span><span class="sxs-lookup"><span data-stu-id="c7fd2-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="c7fd2-111">Você pode especificar um padrão **DataTableMapping** criando um **DataTableMapping** com o nome de "Table".</span><span class="sxs-lookup"><span data-stu-id="c7fd2-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="c7fd2-112">O exemplo de código a seguir cria uma **DataTableMapping** (da <xref:System.Data.Common> namespace) e torna o mapeamento padrão para especificado **DataAdapter** ao nomeá-lo "Table".</span><span class="sxs-lookup"><span data-stu-id="c7fd2-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="c7fd2-113">O exemplo, em seguida, mapeia as colunas da primeira tabela no resultado da consulta (o **clientes** tabela da **Northwind** banco de dados) para um conjunto de nomes mais amigáveis no **clientes Northwind**  na tabela a <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c7fd2-114">Para colunas que não são mapeadas, o nome da coluna na fonte de dados é usado.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =   
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 <span data-ttu-id="c7fd2-115">Em situações mais avançadas, você pode decidir que deseja que o mesmo **DataAdapter** para dar suporte ao carregamento de diferentes tabelas com diferentes mapeamentos.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="c7fd2-116">Para fazer isso, basta adicionar mais **DataTableMapping** objetos.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="c7fd2-117">Quando o **preencher** método recebe uma instância de um **DataSet** e um **DataTableMapping** nome, se existir um mapeamento com esse nome, ele é usado; caso contrário, um  **DataTable** com esse nome é usado.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="c7fd2-118">Os exemplos a seguir criam uma **DataTableMapping** com um nome de **clientes** e um **DataTable** nome do **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="c7fd2-119">O exemplo, em seguida, mapeia as linhas retornadas pela instrução SELECT para o **BizTalkSchema** **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =   
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
>  <span data-ttu-id="c7fd2-120">Se o nome de uma coluna de origem não for fornecido para um mapeamento de coluna ou se o nome de uma tabela de origem não for fornecido para um mapeamento de tabela, os nomes padrão serão gerados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="c7fd2-121">Se nenhuma coluna de origem é fornecida para um mapeamento de coluna, o mapeamento de coluna recebe um nome padrão incremental **SourceColumn** *N,* começando com **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="c7fd2-122">Se nenhum nome de tabela de origem é fornecido para um mapeamento de tabela, o mapeamento de tabela é fornecido um nome padrão incremental **SourceTable** *N*, começando com **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7fd2-123">É recomendável que você evite a convenção de nomeação **SourceColumn** *N* para um mapeamento de coluna, ou **SourceTable** *N* para uma tabela mapeamento, porque o nome fornecido pode entrar em conflito com um nome de mapeamento de coluna padrão existente na **ColumnMappingCollection** ou o nome do mapeamento de tabela na **DataTableMappingCollection** .</span><span class="sxs-lookup"><span data-stu-id="c7fd2-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="c7fd2-124">Se o nome fornecido já existir, será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="c7fd2-125">Manipulando vários conjuntos de resultados</span><span class="sxs-lookup"><span data-stu-id="c7fd2-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="c7fd2-126">Se sua **SelectCommand** retorna várias tabelas, **preencher** gera automaticamente os nomes de tabela com valores incrementais para as tabelas a **conjunto de dados**, começando com o especificado o nome de tabela e continuando no formulário **TableName** *N*, começando com **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="c7fd2-127">Você pode usar mapeamentos de tabela para mapear o nome de tabela gerado automaticamente para um nome que você deseja especificado para a tabela na **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="c7fd2-128">Por exemplo, para um **SelectCommand** , duas tabelas, que retorna **clientes** e **pedidos**, emita a seguinte chamada para **preencher**.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 <span data-ttu-id="c7fd2-129">Duas tabelas são criadas na **conjunto de dados**: **Os clientes** e **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="c7fd2-130">Você pode usar mapeamentos de tabela para garantir que a segunda tabela é denominada **pedidos** em vez de **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="c7fd2-131">Para fazer isso, mapeie a tabela de origem do **Customers1** para o **DataSet** tabela **pedidos**, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7fd2-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7fd2-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7fd2-132">See also</span></span>
- [<span data-ttu-id="c7fd2-133">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="c7fd2-133">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- <span data-ttu-id="c7fd2-134">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c7fd2-134">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="c7fd2-135">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c7fd2-135">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
