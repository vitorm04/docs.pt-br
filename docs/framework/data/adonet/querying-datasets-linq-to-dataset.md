---
title: Consultando DataSets (LINQ to DataSet)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c9830587e70d7671200fac20c8384f1a470a751e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="195fc-102">Consultando DataSets (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="195fc-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="195fc-103">Depois que um objeto de <xref:System.Data.DataSet> foi populado com dados, você pode começar a consulta.</span><span class="sxs-lookup"><span data-stu-id="195fc-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="195fc-104">A formulação de consultas com o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] é semelhante ao uso do [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] em outra fonte de dados habilitada para [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="195fc-104">Formulating queries with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="195fc-105">Lembre-se, no entanto, que quando você usar [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consultas sobre um <xref:System.Data.DataSet> objeto que você está consultando uma enumeração de <xref:System.Data.DataRow> objetos, em vez de uma enumeração de um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="195fc-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="195fc-106">Isso significa que você pode usar qualquer um dos membros a <xref:System.Data.DataRow> classe em seu [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consultas.</span><span class="sxs-lookup"><span data-stu-id="195fc-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="195fc-107">Isso permite criar consultas avançadas e complexas.</span><span class="sxs-lookup"><span data-stu-id="195fc-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="195fc-108">Assim como outras implementações do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], você pode criar [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consultas em duas formas diferentes: sintaxe de consulta com base em método e sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="195fc-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="195fc-109">Para obter mais informações sobre essas duas formas, consulte [Introdução a LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span><span class="sxs-lookup"><span data-stu-id="195fc-109">For more information about these two forms, see [Getting Started with LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span></span> <span data-ttu-id="195fc-110">Você pode usar a sintaxe de expressão de consulta ou sintaxe de consulta com base em método para executar consultas em tabelas único em uma <xref:System.Data.DataSet>, em relação a várias tabelas em um <xref:System.Data.DataSet>, ou em tabelas em um tipo <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="195fc-110">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="195fc-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="195fc-111">In This Section</span></span>  
 [<span data-ttu-id="195fc-112">Consultas de tabela única</span><span class="sxs-lookup"><span data-stu-id="195fc-112">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="195fc-113">Descreve como executar consultas em uma única tabela.</span><span class="sxs-lookup"><span data-stu-id="195fc-113">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="195fc-114">Consultas de tabela cruzada</span><span class="sxs-lookup"><span data-stu-id="195fc-114">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="195fc-115">Descreve como executar consultas em tabelas cruzadas.</span><span class="sxs-lookup"><span data-stu-id="195fc-115">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="195fc-116">Consultando DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="195fc-116">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 <span data-ttu-id="195fc-117">Descreve como consultar objetos <xref:System.Data.DataSet> tipados.</span><span class="sxs-lookup"><span data-stu-id="195fc-117">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="195fc-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="195fc-118">See Also</span></span>  
 [<span data-ttu-id="195fc-119">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="195fc-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="195fc-120">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="195fc-120">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
