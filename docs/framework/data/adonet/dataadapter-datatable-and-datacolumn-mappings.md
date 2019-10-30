---
title: Mapeamentos de DataTable e de DataColumn do DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: a9c81c8554c0fb393c10ed69f84c8b2d936ec1e6
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040125"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="11955-102">Mapeamentos de DataTable e de DataColumn do DataAdapter</span><span class="sxs-lookup"><span data-stu-id="11955-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="11955-103">Um **DataAdapter** contém uma coleção de zero ou mais objetos <xref:System.Data.Common.DataTableMapping> em sua propriedade **TableMappings** .</span><span class="sxs-lookup"><span data-stu-id="11955-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="11955-104">Um **DataTableMapping** fornece um mapeamento mestre entre os dados retornados de uma consulta em relação a uma fonte de dados e um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="11955-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="11955-105">O nome de **DataTableMapping** pode ser passado no lugar do nome **DataTable** para o método **Fill** do **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="11955-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="11955-106">O exemplo a seguir cria um **DataTableMapping** chamado **AuthorsMapping** para a tabela **Authors** .</span><span class="sxs-lookup"><span data-stu-id="11955-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="11955-107">Um **DataTableMapping** permite que você use nomes de coluna em uma **DataTable** que são diferentes daquelas no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="11955-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="11955-108">O **DataAdapter** usa o mapeamento para corresponder as colunas quando a tabela é atualizada.</span><span class="sxs-lookup"><span data-stu-id="11955-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="11955-109">Se você não especificar um nome de **tabela** ou de **DataTableMapping** ao chamar o método **Fill** ou **Update** do **DataAdapter**, o **DataAdapter** procurará um **DataTableMapping** chamado "Table".</span><span class="sxs-lookup"><span data-stu-id="11955-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="11955-110">Se esse **DataTableMapping** não existir, o **TableName** da **DataTable** será "Table".</span><span class="sxs-lookup"><span data-stu-id="11955-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="11955-111">Você pode especificar um **DataTableMapping** padrão criando um **DataTableMapping** com o nome "Table".</span><span class="sxs-lookup"><span data-stu-id="11955-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="11955-112">O exemplo de código a seguir cria um **DataTableMapping** (do namespace <xref:System.Data.Common>) e o torna o mapeamento padrão para o **DataAdapter** especificado, nomeando-o como "Table".</span><span class="sxs-lookup"><span data-stu-id="11955-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="11955-113">Em seguida, o exemplo mapeia as colunas da primeira tabela no resultado da consulta (a tabela **Customers** do banco de dados **Northwind** ) para um conjunto de nomes mais amigáveis na tabela **clientes Northwind** na <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="11955-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="11955-114">Para colunas que não são mapeadas, o nome da coluna na fonte de dados é usado.</span><span class="sxs-lookup"><span data-stu-id="11955-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="11955-115">Em situações mais avançadas, você pode decidir que deseja que o mesmo **DataAdapter** dê suporte ao carregamento de tabelas diferentes com mapeamentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="11955-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="11955-116">Para fazer isso, basta adicionar outros objetos **DataTableMapping** .</span><span class="sxs-lookup"><span data-stu-id="11955-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="11955-117">Quando o método **Fill** passa uma instância de um conjunto de um **DataSet** e um nome **DataTableMapping** , se um mapeamento com esse nome já existir, ele será usado; caso contrário, será usada uma **DataTable** com esse nome.</span><span class="sxs-lookup"><span data-stu-id="11955-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="11955-118">Os exemplos a seguir criam um **DataTableMapping** com um nome de **Customers** e um nome **DataTable** de **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="11955-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="11955-119">Em seguida, o exemplo mapeia as linhas retornadas pela instrução SELECT para a **DataTable** **BizTalkSchema** .</span><span class="sxs-lookup"><span data-stu-id="11955-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
> <span data-ttu-id="11955-120">Se o nome de uma coluna de origem não for fornecido para um mapeamento de coluna ou se o nome de uma tabela de origem não for fornecido para um mapeamento de tabela, os nomes padrão serão gerados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="11955-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="11955-121">Se nenhuma coluna de origem for fornecida para um mapeamento de coluna, o mapeamento de coluna receberá um nome padrão incremental de **SourceColumn** *N,* começando com **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="11955-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="11955-122">Se nenhum nome de tabela de origem for fornecido para um mapeamento de tabela, o mapeamento de tabela receberá um nome padrão incremental de **SourceTable** *N*, começando com **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="11955-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11955-123">Recomendamos que você evite a Convenção de nomenclatura de **SourceColumn** *N* para um mapeamento de coluna ou **SourceTable** *n* para um mapeamento de tabela, pois o nome que você fornece pode entrar em conflito com um nome de mapeamento de coluna padrão existente no  **ColumnMappingcollection** ou nome de mapeamento de tabela no **DataTableMappingCollection**.</span><span class="sxs-lookup"><span data-stu-id="11955-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="11955-124">Se o nome fornecido já existir, será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="11955-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="11955-125">Manipulando vários conjuntos de resultados</span><span class="sxs-lookup"><span data-stu-id="11955-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="11955-126">Se o **SelectCommand** retornar várias tabelas, **Fill** gerará automaticamente nomes de tabela com valores incrementais para as tabelas no **conjunto**de valores, começando com o nome da tabela especificada e continuando no formato **TableName** *N*, começando com **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="11955-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="11955-127">Você pode usar mapeamentos de tabela para mapear o nome de tabela gerado automaticamente para um nome que você deseja especificar para a tabela no **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="11955-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="11955-128">Por exemplo, para um **SelectCommand** que retorna duas tabelas, **Customers** e **Orders**, emita a seguinte chamada para **Fill**.</span><span class="sxs-lookup"><span data-stu-id="11955-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="11955-129">Duas tabelas são criadas no **conjunto de conjuntos**: **Customers** e **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="11955-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="11955-130">Você pode usar mapeamentos de tabela para garantir que a segunda tabela seja denominada **Orders** em vez de **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="11955-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="11955-131">Para fazer isso, mapeie a tabela de origem de **Customers1** para os **pedidos**de tabela de **conjunto** de tabelas, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="11955-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="11955-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11955-132">See also</span></span>

- [<span data-ttu-id="11955-133">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="11955-133">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- <span data-ttu-id="11955-134">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="11955-134">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="11955-135">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="11955-135">[ADO.NET Overview](ado-net-overview.md)</span></span>
