---
title: Formular junções e consultas entre produtos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: a06c7d451d9ad2856092910065f1195a86c737ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548502"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="1cdab-102">Formular junções e consultas entre produtos</span><span class="sxs-lookup"><span data-stu-id="1cdab-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="1cdab-103">Os exemplos a seguir mostram como combinar resultados de várias tabelas.</span><span class="sxs-lookup"><span data-stu-id="1cdab-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cdab-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cdab-104">Example</span></span>  
 <span data-ttu-id="1cdab-105">O exemplo a seguir usa a navegação de chave estrangeira na `From` cláusula no Visual Basic (`from` cláusula C#) para selecionar todos os pedidos de clientes em Londres.</span><span class="sxs-lookup"><span data-stu-id="1cdab-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="1cdab-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cdab-106">Example</span></span>  
 <span data-ttu-id="1cdab-107">O exemplo a seguir usa a navegação de chave estrangeira na `Where` cláusula no Visual Basic (`where` cláusula C#) para filtrar de indisponibilidade de estoque `Products` cujo `Supplier` está nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="1cdab-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="1cdab-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cdab-108">Example</span></span>  
 <span data-ttu-id="1cdab-109">O exemplo a seguir usa a navegação de chave estrangeira na `From` cláusula no Visual Basic (`from` cláusula C#) para filtrar funcionários em Seattle e listar seus territórios.</span><span class="sxs-lookup"><span data-stu-id="1cdab-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="1cdab-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cdab-110">Example</span></span>  
 <span data-ttu-id="1cdab-111">O exemplo a seguir usa a navegação de chave estrangeira na `Select` cláusula no Visual Basic (`select` cláusula C#) para filtrar pares de funcionários onde um funcionário se reporta ao outro e onde ambos os funcionários são da mesma `City`.</span><span class="sxs-lookup"><span data-stu-id="1cdab-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="1cdab-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cdab-112">Example</span></span>  
 <span data-ttu-id="1cdab-113">O exemplo de Visual Basic a seguir procura todos os clientes e pedidos, torna-se de que os pedidos correspondem aos clientes e garante que, para cada cliente na lista, é fornecido um nome de contato.</span><span class="sxs-lookup"><span data-stu-id="1cdab-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="1cdab-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cdab-114">Example</span></span>  
 <span data-ttu-id="1cdab-115">O exemplo a seguir une explicitamente duas tabelas e os resultados dos projetos das duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="1cdab-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="1cdab-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cdab-116">Example</span></span>  
 <span data-ttu-id="1cdab-117">O exemplo a seguir une explicitamente três tabelas e os resultados dos projetos de cada uma delas.</span><span class="sxs-lookup"><span data-stu-id="1cdab-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="1cdab-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cdab-118">Example</span></span>  
 <span data-ttu-id="1cdab-119">O exemplo a seguir mostra como obter um `LEFT OUTER JOIN` usando `DefaultIfEmpty()`.</span><span class="sxs-lookup"><span data-stu-id="1cdab-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="1cdab-120">O método `DefaultIfEmpty()` retorna nulo quando não há nenhum `Order` para o `Employee`.</span><span class="sxs-lookup"><span data-stu-id="1cdab-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="1cdab-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cdab-121">Example</span></span>  
 <span data-ttu-id="1cdab-122">O exemplo a seguir projeta uma expressão `let` resultante de uma junção.</span><span class="sxs-lookup"><span data-stu-id="1cdab-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="1cdab-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cdab-123">Example</span></span>  
 <span data-ttu-id="1cdab-124">O exemplo a seguir mostra um `join` com uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="1cdab-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="1cdab-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1cdab-125">Example</span></span>  
 <span data-ttu-id="1cdab-126">O exemplo a seguir mostra como construir um `join` onde um lado é anulável e o outro não.</span><span class="sxs-lookup"><span data-stu-id="1cdab-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="1cdab-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cdab-127">See also</span></span>
- [<span data-ttu-id="1cdab-128">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="1cdab-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
