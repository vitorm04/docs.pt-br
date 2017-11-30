---
title: Consultando DataSets tipados
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
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bd78b4f47d7f48d7b4cbacdf53140758a05b7869
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="querying-typed-datasets"></a><span data-ttu-id="95d29-102">Consultando DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="95d29-102">Querying Typed DataSets</span></span>
<span data-ttu-id="95d29-103">Se o esquema do <xref:System.Data.DataSet> for conhecido no tempo de design do aplicativo, recomendamos usar um <xref:System.Data.DataSet> tipado ao usar o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95d29-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="95d29-104">Um tipo <xref:System.Data.DataSet> é uma classe que deriva de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="95d29-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="95d29-105">Como tal, herda todos os métodos, eventos e propriedades de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="95d29-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="95d29-106">Além disso, um tipo <xref:System.Data.DataSet> fornece métodos com rigidez de tipos, propriedades e eventos.</span><span class="sxs-lookup"><span data-stu-id="95d29-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="95d29-107">Isso significa que você pode acessar tabelas e colunas pelo nome, em vez de usar métodos baseados em coleção.</span><span class="sxs-lookup"><span data-stu-id="95d29-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="95d29-108">Isso torna as consultas mais simples e mais legíveis.</span><span class="sxs-lookup"><span data-stu-id="95d29-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="95d29-109">Para obter mais informações, consulte [DataSets tipados](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="95d29-109">For more information, see [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="95d29-110">também oferece suporte a consultas em um tipo <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="95d29-110"> also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="95d29-111">Com um tipo <xref:System.Data.DataSet>, você não precisa usar o genérico <xref:System.Data.DataRowExtensions.Field%2A> método ou <xref:System.Data.DataRowExtensions.SetField%2A> método para acessar dados de coluna.</span><span class="sxs-lookup"><span data-stu-id="95d29-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span>  <span data-ttu-id="95d29-112">Nomes de propriedade estão disponíveis em tempo de compilação porque o tipo de informação está incluído no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="95d29-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="95d29-113">fornece acesso aos valores de coluna como o tipo correto, para que os erros de incompatibilidade de tipo são detectados quando o código é compilado em vez de em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="95d29-113"> provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>  
  
 <span data-ttu-id="95d29-114">Para que você possa começar a consultar um <xref:System.Data.DataSet> tipado, você deve gerar a classe usando o Designer de Conjunto de Dados no [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95d29-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the DataSet Designer in [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].</span></span>  <span data-ttu-id="95d29-115">Para obter mais informações, consulte [Create and configure datasets (Criar e configurar conjuntos de dados)](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="95d29-115">For more information, see [Create and configure datasets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95d29-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95d29-116">Example</span></span>  
 <span data-ttu-id="95d29-117">O exemplo a seguir mostra uma consulta sobre um <xref:System.Data.DataSet> tipado:</span><span class="sxs-lookup"><span data-stu-id="95d29-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>  
  
```csharp  
var query = from o in orders  
            where o.OnlineOrderFlag == true  
            select new { o.SalesOrderID,  
                         o.OrderDate,  
                         o.SalesOrderNumber };  
  
foreach(var order in query)   
{  
    Console.WriteLine("{0}\t{1:d}\t{2}",   
order.SalesOrderID,   
order.OrderDate,   
order.SalesOrderNumber);  
}  
```  
  
```vb  
Dim orders = ds.Tables("SalesOrderHeader")  
  
Dim query = _  
       From o In orders _  
       Where o.OnlineOrderFlag = True _  
       Select New {SalesOrderID := o.SalesOrderID, _  
                   OrderDate := o.OrderDate, _  
                   SalesOrderNumber := o.SalesOrderNumber}  
  
For Each Dim onlineOrder In query  
 Console.WriteLine("{0}\t{1:d}\t{2}", _  
 onlineOrder.SalesOrderID, _  
 onlineOrder.OrderDate, _  
 onlineOrder.SalesOrderNumber)  
Next  
```  
  
## <a name="see-also"></a><span data-ttu-id="95d29-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95d29-118">See Also</span></span>  
 [<span data-ttu-id="95d29-119">Consultando DataSets</span><span class="sxs-lookup"><span data-stu-id="95d29-119">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="95d29-120">Consultas de tabela cruzada</span><span class="sxs-lookup"><span data-stu-id="95d29-120">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [<span data-ttu-id="95d29-121">Consultas de tabela única</span><span class="sxs-lookup"><span data-stu-id="95d29-121">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
