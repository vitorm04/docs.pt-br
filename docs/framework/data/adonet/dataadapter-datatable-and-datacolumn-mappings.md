---
title: Mapeamentos de DataTable e de DataColumn do DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6380dd0512bd7834f50b87f90f445cb01b7a8b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151553"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="519be-102">Mapeamentos de DataTable e de DataColumn do DataAdapter</span><span class="sxs-lookup"><span data-stu-id="519be-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="519be-103">Um **DataAdapter** contém uma coleção <xref:System.Data.Common.DataTableMapping> de zero ou mais objetos em sua propriedade **TableMappings.**</span><span class="sxs-lookup"><span data-stu-id="519be-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="519be-104">Um **DataTableMapping** fornece um mapeamento mestre entre os dados retornados de <xref:System.Data.DataTable>uma consulta contra uma fonte de dados e um .</span><span class="sxs-lookup"><span data-stu-id="519be-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="519be-105">O nome **DataTableMapping** pode ser passado no lugar do nome **DataTable** para o método **Preenchimento** do **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="519be-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="519be-106">O exemplo a seguir cria um **DataTableMapping** chamado **AuthorsMapping** para a tabela **Autores.**</span><span class="sxs-lookup"><span data-stu-id="519be-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="519be-107">Um **DataTableMapping** permite que você use nomes de coluna **satisfazem** uma Tabela de Dados diferente sustais das do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="519be-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="519be-108">O **DataAdapter** usa o mapeamento para corresponder às colunas quando a tabela é atualizada.</span><span class="sxs-lookup"><span data-stu-id="519be-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="519be-109">Se você não especificar um **nome de tabela** ou um nome **DataTableMapping** ao chamar o método **Preenchimento** ou **Atualização** do **DataAdapter,** o **DataAdapter** procurará um **DataTableMapping** chamado "Table".</span><span class="sxs-lookup"><span data-stu-id="519be-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="519be-110">Se esse **DataTableMapping** não existir, a **TabelaNome** da Tabela de **Dados** será "Tabela".</span><span class="sxs-lookup"><span data-stu-id="519be-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="519be-111">Você pode especificar um **DataTableMapping** padrão criando um **DataTableMapping** com o nome de "Tabela".</span><span class="sxs-lookup"><span data-stu-id="519be-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="519be-112">O exemplo de código a seguir <xref:System.Data.Common> cria um **DataTableMapping** (a partir do namespace) e torna-o o mapeamento padrão para o **DataAdapter** especificado, nomeando-o "Tabela".</span><span class="sxs-lookup"><span data-stu-id="519be-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="519be-113">O exemplo, então, mapeia as colunas da primeira tabela no resultado da consulta (a tabela **Clientes** do banco <xref:System.Data.DataSet>de dados **Northwind)** para um conjunto de nomes mais fáceis de usar na tabela **Clientes Northwind** na .</span><span class="sxs-lookup"><span data-stu-id="519be-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="519be-114">Para colunas que não são mapeadas, o nome da coluna na fonte de dados é usado.</span><span class="sxs-lookup"><span data-stu-id="519be-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="519be-115">Em situações mais avançadas, você pode decidir que deseja que o mesmo **DataAdapter** suporte o carregamento de diferentes tabelas com diferentes mapeamentos.</span><span class="sxs-lookup"><span data-stu-id="519be-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="519be-116">Para fazer isso, basta adicionar objetos adicionais **do DataTableMapping.**</span><span class="sxs-lookup"><span data-stu-id="519be-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="519be-117">Quando o método **Preenchimento** é aprovado uma instância de um **dataset** e um nome **DataTableMapping,** se um mapeamento com esse nome existir, ele será usado; caso contrário, uma **DataTable** com esse nome é usada.</span><span class="sxs-lookup"><span data-stu-id="519be-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="519be-118">Os exemplos a seguir criam um **DataTableMapping** com um nome de **Clientes** e um nome **de DataTable** de **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="519be-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="519be-119">O exemplo, então, mapeia as linhas retornadas pela declaração SELECT para a Tabela **de Dados** **BizTalkSchema** .</span><span class="sxs-lookup"><span data-stu-id="519be-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
> <span data-ttu-id="519be-120">Se o nome de uma coluna de origem não for fornecido para um mapeamento de coluna ou se o nome de uma tabela de origem não for fornecido para um mapeamento de tabela, os nomes padrão serão gerados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="519be-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="519be-121">Se nenhuma coluna de origem for fornecida para um mapeamento de coluna, o mapeamento da coluna recebe um nome padrão incremental da **SourceColumn** *N,* começando com **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="519be-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="519be-122">Se nenhum nome de tabela de origem for fornecido para um mapeamento de tabela, o mapeamento da tabela recebe um nome padrão incremental de **SourceTable** *N*, começando com **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="519be-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="519be-123">Recomendamos que você evite a convenção de nomeação da **SourceColumn** *N* para um mapeamento de coluna, ou **SourceTable** *N* para um mapeamento de tabela, porque o nome que você fornece pode entrar em conflito com um nome de mapeamento de coluna padrão existente no **ColumnMappingCollection** ou nome de mapeamento de tabela na **DataTableMappingCollection**.</span><span class="sxs-lookup"><span data-stu-id="519be-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="519be-124">Se o nome fornecido já existir, será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="519be-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="519be-125">Manipulando vários conjuntos de resultados</span><span class="sxs-lookup"><span data-stu-id="519be-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="519be-126">Se o **SelectCommand** retornar várias tabelas, **o Fill** gerará automaticamente nomes de tabela com valores incrementais para as tabelas no **Conjunto de Dados,** começando com o nome da tabela especificado e continuando no formulário **TableName** *N*, começando com **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="519be-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="519be-127">Você pode usar mapeamentos de tabela para mapear o nome da tabela gerado automaticamente para um nome que você deseja especificado para a tabela no **Conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="519be-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="519be-128">Por exemplo, para um **SelectCommand** que retorna duas **tabelas, Clientes** e **Pedidos,** emita a seguinte chamada para **preencher**.</span><span class="sxs-lookup"><span data-stu-id="519be-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="519be-129">Duas tabelas são criadas no **DataSet**: **Clientes** e **Clientes1**.</span><span class="sxs-lookup"><span data-stu-id="519be-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="519be-130">Você pode usar mapeamentos de tabela para garantir que a segunda tabela seja nomeada **Orders** em vez de **Clientes1**.</span><span class="sxs-lookup"><span data-stu-id="519be-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="519be-131">Para isso, mapeie a tabela de origem dos **Clientes1** para as **ordens**da tabela **DataSet,** conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="519be-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="519be-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="519be-132">See also</span></span>

- [<span data-ttu-id="519be-133">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="519be-133">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- <span data-ttu-id="519be-134">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="519be-134">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md)</span></span>
- [<span data-ttu-id="519be-135">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="519be-135">ADO.NET Overview</span></span>](ado-net-overview.md)
