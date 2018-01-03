---
title: Navegando em DataRelations
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
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d7d1dc98bdb235c6501ee503494d3c2bdc3a1820
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="navigating-datarelations"></a><span data-ttu-id="6f80c-102">Navegando em DataRelations</span><span class="sxs-lookup"><span data-stu-id="6f80c-102">Navigating DataRelations</span></span>
<span data-ttu-id="6f80c-103">Uma das principais funções de um <xref:System.Data.DataRelation> é permitir a navegação de um <xref:System.Data.DataTable> para outro em um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="6f80c-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6f80c-104">Isso permite que você recupere todos relacionado <xref:System.Data.DataRow> objetos em um **DataTable** quando é fornecido um único **DataRow** de um relacionados **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="6f80c-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="6f80c-105">Por exemplo, depois de estabelecer um **DataRelation** entre uma tabela de clientes e uma tabela de pedidos, você pode recuperar todas as linhas de ordem para uma linha de cliente específico usando **GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="6f80c-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="6f80c-106">O exemplo de código a seguir cria um **DataRelation** entre o **clientes** tabela e o **pedidos** tabela de uma **conjunto de dados** e retorna todos os pedidos para cada cliente.</span><span class="sxs-lookup"><span data-stu-id="6f80c-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="6f80c-107">O exemplo a seguir se baseia no exemplo anterior, relacionando quatro tabelas juntas e navegando nessas relações.</span><span class="sxs-lookup"><span data-stu-id="6f80c-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="6f80c-108">Como no exemplo anterior, **CustomerID** relaciona o **clientes** de tabela para o **pedidos** tabela.</span><span class="sxs-lookup"><span data-stu-id="6f80c-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="6f80c-109">Para cada cliente no **clientes** tabela, todas as linhas filho no **pedidos** tabela são determinados, para retornar o número de pedidos de um cliente específico tiver e seus **OrderID** valores.</span><span class="sxs-lookup"><span data-stu-id="6f80c-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="6f80c-110">O exemplo expandido também retorna os valores da **OrderDetails** e **produtos** tabelas.</span><span class="sxs-lookup"><span data-stu-id="6f80c-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="6f80c-111">O **pedidos** tabela está relacionada ao **OrderDetails** tabela usando **OrderID** para determinar para cada pedido do cliente, que produtos e quantidades foram solicitadas.</span><span class="sxs-lookup"><span data-stu-id="6f80c-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="6f80c-112">Porque o **OrderDetails** tabela contém apenas o **ProductID** de um produto pedido, **OrderDetails** está relacionado à **produtos** usando **ProductID** para retornar o **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="6f80c-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="6f80c-113">Nessa relação, o **produtos** tabela é o pai e o **Order Details** tabela é o filho.</span><span class="sxs-lookup"><span data-stu-id="6f80c-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="6f80c-114">Como resultado, ao fazer a iteração por meio de **OrderDetails** tabela, **GetParentRow** é chamado para recuperar o relacionados **ProductName** valor.</span><span class="sxs-lookup"><span data-stu-id="6f80c-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="6f80c-115">Observe que, quando o **DataRelation** é criado para o **clientes** e **pedidos** tabelas, nenhum valor for especificado para o **createConstraints**sinalizador (o padrão é **true**).</span><span class="sxs-lookup"><span data-stu-id="6f80c-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="6f80c-116">Isso pressupõe que todas as linhas no **pedidos** tabela ter um **CustomerID** valor existe no pai **clientes** tabela.</span><span class="sxs-lookup"><span data-stu-id="6f80c-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="6f80c-117">Se um **CustomerID** existe no **pedidos** que não existe na tabela a **clientes** tabela, um <xref:System.Data.ForeignKeyConstraint> faz com que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="6f80c-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="6f80c-118">Quando a coluna filho pode conter valores que não contém a coluna pai, defina o **createConstraints** sinalizador como **false** ao adicionar o **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="6f80c-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="6f80c-119">No exemplo, o **createConstraints** sinalizador é definido como **false** para o **DataRelation** entre o **pedidos** tabela e o  **OrderDetails** tabela.</span><span class="sxs-lookup"><span data-stu-id="6f80c-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="6f80c-120">Isso permite que o aplicativo retornar todos os registros da **OrderDetails** tabela e apenas um subconjunto de registros da **pedidos** tabela sem gerar uma exceção de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6f80c-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="6f80c-121">O exemplo expandido gera saída no formato a seguir.</span><span class="sxs-lookup"><span data-stu-id="6f80c-121">The expanded sample generates output in the following format.</span></span>  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 <span data-ttu-id="6f80c-122">O exemplo de código a seguir é um exemplo de expandido onde os valores da **OrderDetails** e **produtos** tabelas são retornadas, com apenas um subconjunto dos registros da **pedidos**tabela que está sendo retornada.</span><span class="sxs-lookup"><span data-stu-id="6f80c-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6f80c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f80c-123">See Also</span></span>  
 <span data-ttu-id="6f80c-124">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="6f80c-124">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="6f80c-125">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="6f80c-125">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
