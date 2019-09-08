---
title: Formule projeções
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793822"
---
# <a name="formulate-projections"></a><span data-ttu-id="7f713-102">Formule projeções</span><span class="sxs-lookup"><span data-stu-id="7f713-102">Formulate Projections</span></span>
<span data-ttu-id="7f713-103">Os exemplos a seguir mostram como `select` a instrução C# in `Select` e a instrução no Visual Basic podem ser combinadas com outros recursos para formar projeções de consulta.</span><span class="sxs-lookup"><span data-stu-id="7f713-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f713-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f713-104">Example</span></span>  
 <span data-ttu-id="7f713-105">O exemplo a seguir usa `Select` a cláusula em Visual Basic`select` (cláusula C#in) para retornar uma sequência de nomes de `Customers`contato para.</span><span class="sxs-lookup"><span data-stu-id="7f713-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="7f713-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f713-106">Example</span></span>  
 <span data-ttu-id="7f713-107">O exemplo a seguir usa `Select` a cláusula em Visual Basic`select` (cláusula C#in) e *tipos anônimos* para retornar uma sequência de nomes de contato e `Customers`números de telefone para o.</span><span class="sxs-lookup"><span data-stu-id="7f713-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="7f713-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f713-108">Example</span></span>  
 <span data-ttu-id="7f713-109">O exemplo a seguir usa `Select` a cláusula em Visual Basic`select` (cláusula C#in) e *tipos anônimos* para retornar uma sequência de nomes e números de telefone para os funcionários.</span><span class="sxs-lookup"><span data-stu-id="7f713-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="7f713-110">Os `FirstName` campos `LastName` e são combinados em um único campo (`Name`), e o `HomePhone` campo é renomeado para `Phone` na sequência resultante.</span><span class="sxs-lookup"><span data-stu-id="7f713-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="7f713-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f713-111">Example</span></span>  
 <span data-ttu-id="7f713-112">O exemplo a seguir usa `Select` a cláusula em Visual Basic`select` (cláusula C#in) e *tipos anônimos* para retornar uma sequência `ProductID`de todos os s e um `HalfPrice`valor calculado chamado.</span><span class="sxs-lookup"><span data-stu-id="7f713-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="7f713-113">Esse valor é definido como `UnitPrice` dividido por 2.</span><span class="sxs-lookup"><span data-stu-id="7f713-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="7f713-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f713-114">Example</span></span>  
 <span data-ttu-id="7f713-115">O exemplo a seguir usa `Select` a cláusula em Visual Basic`select` (cláusula C#in) e uma *instrução condicional* para retornar uma sequência de nome do produto e disponibilidade do produto.</span><span class="sxs-lookup"><span data-stu-id="7f713-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="7f713-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f713-116">Example</span></span>  
 <span data-ttu-id="7f713-117">O exemplo a seguir usa uma `Select` cláusula Visual Basic`select` (cláusula C#in) e um *tipo conhecido* (Name) para retornar uma sequência dos nomes dos funcionários.</span><span class="sxs-lookup"><span data-stu-id="7f713-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="7f713-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f713-118">Example</span></span>  
 <span data-ttu-id="7f713-119">O exemplo a seguir `Select` usa `Where` e em Visual Basic`select` ( `where` e C#em) para retornar uma *sequência filtrada* de nomes de contato para clientes em Londres.</span><span class="sxs-lookup"><span data-stu-id="7f713-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="7f713-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f713-120">Example</span></span>  
 <span data-ttu-id="7f713-121">O exemplo a seguir usa `Select` uma cláusula em Visual Basic`select` (cláusula C#in) e *tipos anônimos* para retornar um *subconjunto formatado* dos dados sobre os clientes.</span><span class="sxs-lookup"><span data-stu-id="7f713-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="7f713-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f713-122">Example</span></span>  
 <span data-ttu-id="7f713-123">O exemplo a seguir usa consultas aninhadas para retornar os resultados seguintes:</span><span class="sxs-lookup"><span data-stu-id="7f713-123">The following example uses nested queries to return the following results:</span></span>  
  
- <span data-ttu-id="7f713-124">Uma sequência de todos os pedidos e seu `OrderID`correspondente S.</span><span class="sxs-lookup"><span data-stu-id="7f713-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
- <span data-ttu-id="7f713-125">Um subsequence dos itens na ordem para que há desconto.</span><span class="sxs-lookup"><span data-stu-id="7f713-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
- <span data-ttu-id="7f713-126">A quantidade de caixa salva se os custos de enviar não são incluídos.</span><span class="sxs-lookup"><span data-stu-id="7f713-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="7f713-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f713-127">See also</span></span>

- [<span data-ttu-id="7f713-128">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="7f713-128">Query Examples</span></span>](query-examples.md)
