---
title: 'Exemplos de sintaxe de consulta baseada em método: Projeção'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: 3a9203a51bbb61b32300919656084d7d95ddfa79
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397314"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="f7b5c-102">Exemplos de sintaxe de consulta baseada em método: Projeção</span><span class="sxs-lookup"><span data-stu-id="f7b5c-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="f7b5c-103">Os exemplos neste tópico demonstram como usar os métodos <xref:System.Linq.Enumerable.Select%2A> e <xref:System.Linq.Enumerable.SelectMany%2A> para consultar o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) usando a sintaxe de consulta baseada em método.</span><span class="sxs-lookup"><span data-stu-id="f7b5c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="f7b5c-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f7b5c-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f7b5c-105">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="f7b5c-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="f7b5c-106">Selecionar</span><span class="sxs-lookup"><span data-stu-id="f7b5c-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="f7b5c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7b5c-107">Example</span></span>  
 <span data-ttu-id="f7b5c-108">O exemplo a seguir usa o método <xref:System.Linq.Queryable.Select%2A> para projetar as propriedades `Product.Name` e `Product.ProductID` em uma sequência de tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="f7b5c-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="f7b5c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7b5c-109">Example</span></span>  
 <span data-ttu-id="f7b5c-110">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Select%2A> para retornar somente uma sequência de nomes do produto.</span><span class="sxs-lookup"><span data-stu-id="f7b5c-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="f7b5c-111">SelectMany</span><span class="sxs-lookup"><span data-stu-id="f7b5c-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="f7b5c-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7b5c-112">Example</span></span>  
 <span data-ttu-id="f7b5c-113">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.SelectMany%2A> para selecionar todos os pedidos onde `TotalDue` é menor que 500,00.</span><span class="sxs-lookup"><span data-stu-id="f7b5c-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="f7b5c-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7b5c-114">Example</span></span>  
 <span data-ttu-id="f7b5c-115">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.SelectMany%2A> para selecionar todos os pedidos feitos em 1º de outubro de 2002 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="f7b5c-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="f7b5c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7b5c-116">See also</span></span>

- [<span data-ttu-id="f7b5c-117">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f7b5c-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
