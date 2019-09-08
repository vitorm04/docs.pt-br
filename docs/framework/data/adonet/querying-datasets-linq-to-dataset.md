---
title: Consultando DataSets (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 79a9b320fbdbfecc3f7d531d992b1529873871a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783041"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="c42ae-102">Consultando DataSets (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="c42ae-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="c42ae-103">Depois que um objeto de <xref:System.Data.DataSet> foi populado com dados, você pode começar a consulta.</span><span class="sxs-lookup"><span data-stu-id="c42ae-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="c42ae-104">Formular consultas com LINQ to DataSet é semelhante ao uso [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] de outras [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]fontes de dados habilitadas para outras.</span><span class="sxs-lookup"><span data-stu-id="c42ae-104">Formulating queries with LINQ to DataSet is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="c42ae-105">No entanto, lembre-se de [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] que, ao <xref:System.Data.DataSet> usar consultas em um objeto, você está <xref:System.Data.DataRow> consultando uma enumeração de objetos, em vez de uma enumeração de um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="c42ae-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="c42ae-106">Isso significa que você pode usar qualquer um dos membros da <xref:System.Data.DataRow> classe em suas [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consultas.</span><span class="sxs-lookup"><span data-stu-id="c42ae-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="c42ae-107">Isso permite que você crie consultas sofisticadas e complexas.</span><span class="sxs-lookup"><span data-stu-id="c42ae-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="c42ae-108">Assim como acontece com outras [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]implementações do, você pode criar LINQ to DataSet consultas em duas formas diferentes: sintaxe de expressão de consulta e sintaxe de consulta baseada em método.</span><span class="sxs-lookup"><span data-stu-id="c42ae-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="c42ae-109">Você pode usar sintaxe de expressão de consulta ou sintaxe de consulta baseada em método para executar consultas em tabelas <xref:System.Data.DataSet>únicas em um, em relação <xref:System.Data.DataSet>a várias tabelas em uma ou em <xref:System.Data.DataSet>tabelas em um tipo.</span><span class="sxs-lookup"><span data-stu-id="c42ae-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c42ae-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c42ae-110">In This Section</span></span>  
 [<span data-ttu-id="c42ae-111">Consultas de tabela única</span><span class="sxs-lookup"><span data-stu-id="c42ae-111">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="c42ae-112">Descreve como executar consultas em uma única tabela.</span><span class="sxs-lookup"><span data-stu-id="c42ae-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="c42ae-113">Consultas de tabela cruzada</span><span class="sxs-lookup"><span data-stu-id="c42ae-113">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="c42ae-114">Descreve como executar consultas em tabelas cruzadas.</span><span class="sxs-lookup"><span data-stu-id="c42ae-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="c42ae-115">Consultando DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="c42ae-115">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="c42ae-116">Descreve como consultar objetos <xref:System.Data.DataSet> tipados.</span><span class="sxs-lookup"><span data-stu-id="c42ae-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c42ae-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c42ae-117">See also</span></span>

- [<span data-ttu-id="c42ae-118">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c42ae-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="c42ae-119">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="c42ae-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
