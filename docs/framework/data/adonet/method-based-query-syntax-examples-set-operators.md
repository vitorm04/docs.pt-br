---
title: 'Exemplos de sintaxe de consulta baseada em método: Definir operadores (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 481c0ed7e39b8f958ccdae01e4589d54b3ff2446
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783581"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="0e166-102">Exemplos de sintaxe de consulta baseada em método: Definir operadores (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0e166-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="0e166-103">Os exemplos neste <xref:System.Linq.Enumerable.Distinct%2A>tópico demonstram como usar os operadores <xref:System.Linq.Enumerable.Intersect%2A>, <xref:System.Linq.Enumerable.Except%2A>, e <xref:System.Linq.Enumerable.Union%2A> para executar operações de comparação com base em valores em conjuntos de linhas de dados.[ O carregamento de dados em um DataSet](loading-data-into-a-dataset.md) , consulte comparando [DataRows](comparing-datarows-linq-to-dataset.md) , para obter mais informações sobre <xref:System.Data.DataRowComparer>o.</span><span class="sxs-lookup"><span data-stu-id="0e166-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](loading-data-into-a-dataset.md) See [Comparing DataRows](comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="0e166-104">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="0e166-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="0e166-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0e166-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0e166-106">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="0e166-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="0e166-107">Para obter mais informações, confira [Como: Crie um projeto LINQ to DataSet no Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0e166-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="0e166-108">Distinct</span><span class="sxs-lookup"><span data-stu-id="0e166-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="0e166-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e166-109">Example</span></span>  
 <span data-ttu-id="0e166-110">Este exemplo usa o método de <xref:System.Linq.Enumerable.Distinct%2A> para remover elementos duplicados em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="0e166-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="0e166-111">Exceto</span><span class="sxs-lookup"><span data-stu-id="0e166-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="0e166-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e166-112">Example</span></span>  
 <span data-ttu-id="0e166-113">Este exemplo usa o método de <xref:System.Linq.Enumerable.Except%2A> para retornar os contatos que aparecem na primeira tabela mas não no segundo.</span><span class="sxs-lookup"><span data-stu-id="0e166-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="0e166-114">Interseção</span><span class="sxs-lookup"><span data-stu-id="0e166-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="0e166-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e166-115">Example</span></span>  
 <span data-ttu-id="0e166-116">Este exemplo usa o método de <xref:System.Linq.Enumerable.Intersect%2A> para retornar os contatos que aparecem em ambas as tabelas.</span><span class="sxs-lookup"><span data-stu-id="0e166-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="0e166-117">União</span><span class="sxs-lookup"><span data-stu-id="0e166-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="0e166-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e166-118">Example</span></span>  
 <span data-ttu-id="0e166-119">Este exemplo usa o método de <xref:System.Linq.Enumerable.Union%2A> para retornar contatos exclusivos de uma das duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="0e166-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="0e166-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e166-120">See also</span></span>

- [<span data-ttu-id="0e166-121">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="0e166-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="0e166-122">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="0e166-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="0e166-123">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="0e166-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0e166-124">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e166-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
