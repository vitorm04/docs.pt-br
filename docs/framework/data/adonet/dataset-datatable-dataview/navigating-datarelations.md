---
title: Navegando em DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: b7b1717317bb119538497f60bae48ec1da2286c8
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203331"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="388f3-102">Navegando em DataRelations</span><span class="sxs-lookup"><span data-stu-id="388f3-102">Navigating DataRelations</span></span>
<span data-ttu-id="388f3-103">Uma das principais funções de um <xref:System.Data.DataRelation> é permitir a navegação de um <xref:System.Data.DataTable> para outro em um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="388f3-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="388f3-104">Isso permite que você recupere todos os objetos <xref:System.Data.DataRow> relacionados em uma **DataTable** quando recebe uma única **DataRow** de uma **DataTable**relacionada.</span><span class="sxs-lookup"><span data-stu-id="388f3-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="388f3-105">Por exemplo, depois de estabelecer uma DataRelation entre uma tabela de clientes e uma tabela de pedidos, você pode recuperar todas as linhas de ordem de uma linha de cliente específica usando **GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="388f3-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="388f3-106">O exemplo de código a seguir cria uma DataRelation entre a tabela **Customers** e a tabela **Orders** de um **DataSet** e retorna todos os pedidos para cada cliente.</span><span class="sxs-lookup"><span data-stu-id="388f3-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="388f3-107">O exemplo a seguir se baseia no exemplo anterior, relacionando quatro tabelas juntas e navegando nessas relações.</span><span class="sxs-lookup"><span data-stu-id="388f3-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="388f3-108">Como no exemplo anterior, **CustomerID** relaciona a tabela Customers à tabela Orders .</span><span class="sxs-lookup"><span data-stu-id="388f3-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="388f3-109">Para cada cliente na tabela **Customers** , todas as linhas filho na tabela **Orders** são determinadas para retornar o número de pedidos que um cliente específico tem e seus valores de **OrderID** .</span><span class="sxs-lookup"><span data-stu-id="388f3-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="388f3-110">O exemplo expandido também retorna os valores das tabelas **OrderDetails** e **Products** .</span><span class="sxs-lookup"><span data-stu-id="388f3-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="388f3-111">A tabela **pedidos** está relacionada à tabela **OrderDetails** usando **OrderID** para determinar, para cada pedido de cliente, quais produtos e quantidades foram ordenados.</span><span class="sxs-lookup"><span data-stu-id="388f3-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="388f3-112">Como a tabela **OrderDetails** contém apenas a **ProductID** de um produto ordenado, o **OrderDetails** está relacionado aos **produtos** que usam **ProductID** para retornar o **NomeDoProduto**.</span><span class="sxs-lookup"><span data-stu-id="388f3-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="388f3-113">Nessa relação, a tabela **produtos** é o pai e a tabela **detalhes do pedido** é o filho.</span><span class="sxs-lookup"><span data-stu-id="388f3-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="388f3-114">Como resultado, ao iterar pela tabela **OrderDetails** , **GetParentRow** é chamado para recuperar o valor de **NomeDoProduto** relacionado.</span><span class="sxs-lookup"><span data-stu-id="388f3-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="388f3-115">Observe que, quando a DataRelation é criada para as tabelas **Customers** e **Orders** , nenhum valor é especificado para o sinalizador createConstraints (o padrão é **true**).</span><span class="sxs-lookup"><span data-stu-id="388f3-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="388f3-116">Isso pressupõe que todas as linhas na tabela **Orders** têm um valor **CustomerID** que existe na tabela Parent **Customers** .</span><span class="sxs-lookup"><span data-stu-id="388f3-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="388f3-117">Se um **CustomerID** existir na tabela **Orders** que não existe na tabela **Customers** , um <xref:System.Data.ForeignKeyConstraint> fará com que uma exceção seja gerada.</span><span class="sxs-lookup"><span data-stu-id="388f3-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="388f3-118">Quando a coluna filho pode conter valores que a coluna pai não contém, defina o sinalizador createConstraints como **false** ao adicionar a **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="388f3-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="388f3-119">No exemplo, o sinalizador createConstraints é definido como **false** para a **DataRelation** entre a tabela Orders e a tabela **OrderDetails** .</span><span class="sxs-lookup"><span data-stu-id="388f3-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="388f3-120">Isso permite que o aplicativo retorne todos os registros da tabela **OrderDetails** e apenas um subconjunto de registros da tabela **Orders** sem gerar uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="388f3-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="388f3-121">O exemplo expandido gera saída no formato a seguir.</span><span class="sxs-lookup"><span data-stu-id="388f3-121">The expanded sample generates output in the following format.</span></span>  
  
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
  
 <span data-ttu-id="388f3-122">O exemplo de código a seguir é um exemplo expandido em que os valores das tabelas OrderDetails e **Products** são retornados, com apenas um subconjunto dos registros na tabela **Orders** que está sendo retornada.</span><span class="sxs-lookup"><span data-stu-id="388f3-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="388f3-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="388f3-123">See also</span></span>

- <span data-ttu-id="388f3-124">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="388f3-124">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="388f3-125">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="388f3-125">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
