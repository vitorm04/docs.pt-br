---
title: Consultando DataSets (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: bb64abcffdbbcd46dfb11b2564619c565e461436
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634775"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="11d02-102">Consultando DataSets (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="11d02-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="11d02-103">Depois que um objeto de <xref:System.Data.DataSet> foi populado com dados, você pode começar a consulta.</span><span class="sxs-lookup"><span data-stu-id="11d02-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="11d02-104">Formular consultas com LINQ to DataSet é semelhante ao uso de LINQ (consulta integrada à linguagem) em relação a outras fontes de dados habilitadas para LINQ.</span><span class="sxs-lookup"><span data-stu-id="11d02-104">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="11d02-105">No entanto, lembre-se de que, ao usar consultas LINQ em um objeto <xref:System.Data.DataSet>, você está consultando uma enumeração de objetos <xref:System.Data.DataRow> em vez de uma enumeração de um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="11d02-105">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="11d02-106">Isso significa que você pode usar qualquer um dos membros da classe <xref:System.Data.DataRow> em suas consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="11d02-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="11d02-107">Isso permite que você crie consultas sofisticadas e complexas.</span><span class="sxs-lookup"><span data-stu-id="11d02-107">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="11d02-108">Assim como acontece com outras implementações do LINQ, você pode criar LINQ to DataSet consultas em duas formas diferentes: sintaxe de expressão de consulta e sintaxe de consulta baseada em método.</span><span class="sxs-lookup"><span data-stu-id="11d02-108">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="11d02-109">Você pode usar sintaxe de expressão de consulta ou sintaxe de consulta baseada em método para executar consultas em tabelas únicas em um <xref:System.Data.DataSet>, em várias tabelas em uma <xref:System.Data.DataSet>ou em tabelas em um <xref:System.Data.DataSet>tipado.</span><span class="sxs-lookup"><span data-stu-id="11d02-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11d02-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="11d02-110">In This Section</span></span>  
 [<span data-ttu-id="11d02-111">Consultas de tabela única</span><span class="sxs-lookup"><span data-stu-id="11d02-111">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="11d02-112">Descreve como executar consultas em uma única tabela.</span><span class="sxs-lookup"><span data-stu-id="11d02-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="11d02-113">Consultas de tabela cruzada</span><span class="sxs-lookup"><span data-stu-id="11d02-113">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="11d02-114">Descreve como executar consultas em tabelas cruzadas.</span><span class="sxs-lookup"><span data-stu-id="11d02-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="11d02-115">Consultando DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="11d02-115">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="11d02-116">Descreve como consultar objetos <xref:System.Data.DataSet> tipados.</span><span class="sxs-lookup"><span data-stu-id="11d02-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d02-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="11d02-117">See also</span></span>

- [<span data-ttu-id="11d02-118">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="11d02-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="11d02-119">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="11d02-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
