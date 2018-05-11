---
title: Comparando DataRows (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 79fc91092badfd871a1409e2ee602272f3eae100
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="9f315-102">Comparando DataRows (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="9f315-102">Comparing DataRows (LINQ to DataSet)</span></span>
<span data-ttu-id="9f315-103">O [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] define vários operadores de conjunto para comparar elementos de origem e ver se são iguais.</span><span class="sxs-lookup"><span data-stu-id="9f315-103">[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] defines various set operators to compare source elements to see if they are equal.</span></span> <span data-ttu-id="9f315-104">O [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] fornece os seguintes operadores de conjunto:</span><span class="sxs-lookup"><span data-stu-id="9f315-104">[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] provides the following set operators:</span></span>  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="9f315-105">Esses operadores comparam os elementos de origem chamando os métodos <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> e <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> em cada coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="9f315-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="9f315-106">No caso de <xref:System.Data.DataRow>, esses operadores executam uma comparação de referência, que geralmente não é o comportamento ideal para operações de conjunto em dados de tabela.</span><span class="sxs-lookup"><span data-stu-id="9f315-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="9f315-107">Para operações de conjunto, você geralmente quer determinar se os valores de elementos são iguais, e não as referências de elementos.</span><span class="sxs-lookup"><span data-stu-id="9f315-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="9f315-108">Portanto, a classe <xref:System.Data.DataRowComparer> foi adicionada a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f315-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="9f315-109">Essa classe pode ser usada para comparar valores de linha.</span><span class="sxs-lookup"><span data-stu-id="9f315-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="9f315-110">A classe <xref:System.Data.DataRowComparer> contém uma implementação de comparação de valores para <xref:System.Data.DataRow>, portanto essa classe pode ser usada para operações de conjunto, como <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f315-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="9f315-111">Essa classe não pode ser instanciada diretamente; em vez disso, a propriedade <xref:System.Data.DataRowComparer.Default%2A> deve ser usada para retornar uma instância de <xref:System.Data.DataRowComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="9f315-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="9f315-112">O método <xref:System.Data.DataRowComparer%601.Equals%2A> é então chamado e os dois objetos <xref:System.Data.DataRow> a serem comparados são passados como parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="9f315-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="9f315-113">O método <xref:System.Data.DataRowComparer%601.Equals%2A> retornará `true` se o conjunto ordenado de valores de coluna em ambos os objetos <xref:System.Data.DataRow> forem iguais; caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="9f315-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f315-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f315-114">Example</span></span>  
 <span data-ttu-id="9f315-115">Este exemplo usa `Intersect` para retornar os contatos que aparecem em ambas as tabelas.</span><span class="sxs-lookup"><span data-stu-id="9f315-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="9f315-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f315-116">Example</span></span>  
 <span data-ttu-id="9f315-117">O exemplo a seguir compara duas linhas e obtém seus códigos hash.</span><span class="sxs-lookup"><span data-stu-id="9f315-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="9f315-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f315-118">See Also</span></span>  
 <xref:System.Data.DataRowComparer>  
 [<span data-ttu-id="9f315-119">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="9f315-119">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="9f315-120">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9f315-120">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
