---
title: 'Exemplos de sintaxe de expressão de consulta: Projeção'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: 9c10c334ae2a10df1f75384ce042781b6f1bd43a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178029"
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="c3a33-102">Exemplos de sintaxe de expressão de consulta: Projeção</span><span class="sxs-lookup"><span data-stu-id="c3a33-102">Query Expression Syntax Examples: Projection</span></span>
<span data-ttu-id="c3a33-103">Os exemplos neste tópico demonstram como usar o `Select` método e o `From … From …` palavras-chave para consultar o [modelo de vendas AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) usando a sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="c3a33-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> `From … From …` <span data-ttu-id="c3a33-104">é a consulta com base equivalente a `SelectMany` método.</span><span class="sxs-lookup"><span data-stu-id="c3a33-104">is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="c3a33-105">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c3a33-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c3a33-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="c3a33-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="c3a33-107">Selecionar</span><span class="sxs-lookup"><span data-stu-id="c3a33-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="c3a33-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3a33-108">Example</span></span>  
 <span data-ttu-id="c3a33-109">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Select%2A> para retornar todas as linhas da tabela de `Product` e exibir os nomes de produto.</span><span class="sxs-lookup"><span data-stu-id="c3a33-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="c3a33-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3a33-110">Example</span></span>  
 <span data-ttu-id="c3a33-111">O exemplo a seguir usa <xref:System.Linq.Enumerable.Select%2A> para retornar somente uma sequência de nomes do produto.</span><span class="sxs-lookup"><span data-stu-id="c3a33-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="c3a33-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3a33-112">Example</span></span>  
 <span data-ttu-id="c3a33-113">O exemplo a seguir usa o método <xref:System.Linq.Queryable.Select%2A> para projetar as propriedades `Product.Name` e `Product.ProductID` em uma sequência de tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="c3a33-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="c3a33-114">De...</span><span class="sxs-lookup"><span data-stu-id="c3a33-114">From …</span></span> <span data-ttu-id="c3a33-115">De...</span><span class="sxs-lookup"><span data-stu-id="c3a33-115">From …</span></span> <span data-ttu-id="c3a33-116">(SelectMany)</span><span class="sxs-lookup"><span data-stu-id="c3a33-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="c3a33-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3a33-117">Example</span></span>  
 <span data-ttu-id="c3a33-118">O exemplo a seguir usa `From … From …` (o equivalente do método <xref:System.Linq.Enumerable.SelectMany%2A>) para selecionar todos os pedidos onde `TotalDue` é menor que 500,00.</span><span class="sxs-lookup"><span data-stu-id="c3a33-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="c3a33-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3a33-119">Example</span></span>  
 <span data-ttu-id="c3a33-120">O exemplo a seguir usa `From … From …` (o equivalente do método <xref:System.Linq.Enumerable.SelectMany%2A>) para selecionar todos os pedidos feitos em 1º de outubro de 2002 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="c3a33-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="c3a33-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3a33-121">Example</span></span>  
 <span data-ttu-id="c3a33-122">O exemplo a seguir usa `From … From …` (o equivalente do método <xref:System.Linq.Enumerable.SelectMany%2A>) para selecionar todos os pedidos onde o total do pedido é maior que 10000,00 e usa a atribuição `From` para evitar solicitar o total duas vezes.</span><span class="sxs-lookup"><span data-stu-id="c3a33-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="c3a33-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3a33-123">See also</span></span>

- [<span data-ttu-id="c3a33-124">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c3a33-124">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
