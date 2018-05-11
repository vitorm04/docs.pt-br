---
title: 'Exemplos de sintaxe da consulta com base em método: Definir operadores (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 2c95125182a352d3cd2b0b4c51ffac3f74fff5a7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="bda90-102">Exemplos de sintaxe da consulta com base em método: Definir operadores (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="bda90-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="bda90-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, e <xref:System.Linq.Enumerable.Union%2A> operadores para executar operações de comparação de valor com base em conjuntos de linhas de dados.[ Carregando dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) consulte [comparando DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) para obter mais informações sobre <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="bda90-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) See [Comparing DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="bda90-104">O `FillDataSet` método usado nesses exemplos é especificado em [carregar dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="bda90-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="bda90-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="bda90-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="bda90-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="bda90-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="bda90-107">Para obter mais informações, consulte [como: criar um LINQ to DataSet de projeto no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="bda90-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="bda90-108">Distinct</span><span class="sxs-lookup"><span data-stu-id="bda90-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="bda90-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bda90-109">Example</span></span>  
 <span data-ttu-id="bda90-110">Este exemplo usa o método de <xref:System.Linq.Enumerable.Distinct%2A> para remover elementos duplicados em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="bda90-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="bda90-111">Exceto</span><span class="sxs-lookup"><span data-stu-id="bda90-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="bda90-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bda90-112">Example</span></span>  
 <span data-ttu-id="bda90-113">Este exemplo usa o método de <xref:System.Linq.Enumerable.Except%2A> para retornar os contatos que aparecem na primeira tabela mas não no segundo.</span><span class="sxs-lookup"><span data-stu-id="bda90-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="bda90-114">Interseção</span><span class="sxs-lookup"><span data-stu-id="bda90-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="bda90-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bda90-115">Example</span></span>  
 <span data-ttu-id="bda90-116">Este exemplo usa o método de <xref:System.Linq.Enumerable.Intersect%2A> para retornar os contatos que aparecem em ambas as tabelas.</span><span class="sxs-lookup"><span data-stu-id="bda90-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="bda90-117">União</span><span class="sxs-lookup"><span data-stu-id="bda90-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="bda90-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bda90-118">Example</span></span>  
 <span data-ttu-id="bda90-119">Este exemplo usa o método de <xref:System.Linq.Enumerable.Union%2A> para retornar contatos exclusivos de uma das duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="bda90-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="bda90-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bda90-120">See Also</span></span>  
 [<span data-ttu-id="bda90-121">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="bda90-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="bda90-122">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="bda90-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="bda90-123">Visão Geral de Operadores de Consulta Padrão</span><span class="sxs-lookup"><span data-stu-id="bda90-123">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
