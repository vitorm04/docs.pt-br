---
title: Criando uma DataTable
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
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 923d19e9539c6d93f3714efcdaa6fe7a5da843ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-datatable"></a><span data-ttu-id="da22f-102">Criando uma DataTable</span><span class="sxs-lookup"><span data-stu-id="da22f-102">Creating a DataTable</span></span>
<span data-ttu-id="da22f-103">Uma <xref:System.Data.DataTable>, que representa uma tabela de dados relacionais de memória, pode ser criada e usada independentemente ou pode ser usada por outros objetos do .NET Framework, mais comumente como membro de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="da22f-103">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="da22f-104">Você pode criar um **DataTable** objeto usando a **DataTable** construtor.</span><span class="sxs-lookup"><span data-stu-id="da22f-104">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="da22f-105">Você pode adicioná-lo para o **DataSet** usando o **adicionar** método para adicioná-lo para o **DataTable** do objeto **tabelas** coleção.</span><span class="sxs-lookup"><span data-stu-id="da22f-105">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="da22f-106">Você também pode criar **DataTable** objetos dentro de um **DataSet** usando o **preencher** ou **FillSchema** métodos do  **DataAdapter** objeto, ou de uma predefinida ou inferidos XML esquema usando o **ReadXml**, **ReadXmlSchema**, ou **InferXmlSchema** métodos do **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="da22f-106">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="da22f-107">Observe que depois de ter adicionado uma **DataTable** como um membro do **tabelas** coleção de um **conjunto de dados**, você não pode adicioná-lo à coleção de tabelas de quaisquer outros **Conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="da22f-107">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="da22f-108">Quando você cria primeiro um **DataTable**, ele não tem um esquema (ou seja, uma estrutura).</span><span class="sxs-lookup"><span data-stu-id="da22f-108">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="da22f-109">Para definir o esquema da tabela, você deve criar e adicionar <xref:System.Data.DataColumn> objetos para o **colunas** coleção da tabela.</span><span class="sxs-lookup"><span data-stu-id="da22f-109">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="da22f-110">Você também pode definir uma coluna de chave primária para a tabela e criar e adicionar **restrição** objetos para o **restrições** coleção da tabela.</span><span class="sxs-lookup"><span data-stu-id="da22f-110">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="da22f-111">Depois de definir o esquema para um **DataTable**, você pode adicionar linhas de dados para a tabela adicionando **DataRow** objetos para o **linhas** coleção da tabela.</span><span class="sxs-lookup"><span data-stu-id="da22f-111">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="da22f-112">Não é necessário fornecer um valor para o <xref:System.Data.DataTable.TableName%2A> propriedade quando você cria um **DataTable**; você pode especificar a propriedade em outro momento, ou você pode deixar vazio.</span><span class="sxs-lookup"><span data-stu-id="da22f-112">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="da22f-113">No entanto, quando você adiciona uma tabela sem uma **TableName** valor para um **DataSet**, a tabela terá um nome padrão incremental da tabela*N*, começando com "Tabela" para Table0.</span><span class="sxs-lookup"><span data-stu-id="da22f-113">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da22f-114">É recomendável que você evite a "tabela*N*" convenção de nomenclatura ao fornecer um **TableName** de valor, porque o nome que você fornecer pode entrar em conflito com um nome de tabela padrão existente no **conjunto de dados** .</span><span class="sxs-lookup"><span data-stu-id="da22f-114">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="da22f-115">Se o nome fornecido já existir, será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="da22f-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="da22f-116">O exemplo a seguir cria uma instância de um **DataTable** de objeto e atribui o nome "Clientes".</span><span class="sxs-lookup"><span data-stu-id="da22f-116">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="da22f-117">O exemplo a seguir cria uma instância de um **DataTable** adicionando-o para o **tabelas** coleção de um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="da22f-117">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="da22f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da22f-118">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [<span data-ttu-id="da22f-119">DataTables</span><span class="sxs-lookup"><span data-stu-id="da22f-119">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="da22f-120">[Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)</span><span class="sxs-lookup"><span data-stu-id="da22f-120">[Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)</span></span>  
 [<span data-ttu-id="da22f-121">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="da22f-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="da22f-122">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="da22f-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="da22f-123">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="da22f-123">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
