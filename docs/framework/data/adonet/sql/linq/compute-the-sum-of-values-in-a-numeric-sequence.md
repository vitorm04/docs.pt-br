---
title: Calcular a soma dos valores em uma sequência numérica
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3a404068c2d89610aa9b01b392bca40f82e17707
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247923"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="ace3e-102">Calcular a soma dos valores em uma sequência numérica</span><span class="sxs-lookup"><span data-stu-id="ace3e-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="ace3e-103">Use o operador <xref:System.Linq.Enumerable.Sum%2A> para calcular a soma de valores numéricos em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="ace3e-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="ace3e-104">Observe as seguintes características do operador `Sum` no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ace3e-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="ace3e-105">O operador de agregação do operador de consulta padrão `Sum` avalia uma sequência vazia ou uma sequência que contém somente nulos como zero.</span><span class="sxs-lookup"><span data-stu-id="ace3e-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="ace3e-106">No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a semântica do SQL é deixada inalterada.</span><span class="sxs-lookup"><span data-stu-id="ace3e-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="ace3e-107">Por esse motivo, `Sum` avalia como nulo em vez de zero para uma sequência vazia ou para uma sequência que contém somente nulos.</span><span class="sxs-lookup"><span data-stu-id="ace3e-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
- <span data-ttu-id="ace3e-108">As limitações do SQL em resultados intermediários se aplicam às agregações no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ace3e-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="ace3e-109">A soma das quantidades de inteiros de 32 bits não é calculada usando resultados de 64 bits, e pode ocorrer estouro para [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a tradução `Sum`de.</span><span class="sxs-lookup"><span data-stu-id="ace3e-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="ace3e-110">Essa possibilidade existe mesmo se a implementação do operador de consulta padrão não causa um estouro para a sequência correspondente na memória.</span><span class="sxs-lookup"><span data-stu-id="ace3e-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ace3e-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ace3e-111">Example</span></span>  
 <span data-ttu-id="ace3e-112">O exemplo a seguir localiza o frete total de todos os pedidos na tabela `Order`.</span><span class="sxs-lookup"><span data-stu-id="ace3e-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="ace3e-113">Se você executar essa consulta no banco de dados de exemplo do Northwind, a saída será: `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="ace3e-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="ace3e-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ace3e-114">Example</span></span>  
 <span data-ttu-id="ace3e-115">O exemplo a seguir localiza o número total de unidades no pedido para todos os produtos.</span><span class="sxs-lookup"><span data-stu-id="ace3e-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="ace3e-116">Se você executar essa consulta no banco de dados de exemplo do Northwind, a saída será: `780`.</span><span class="sxs-lookup"><span data-stu-id="ace3e-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="ace3e-117">Observe que você deve converter tipos `short` (por exemplo, `UnitsOnOrder`) porque `Sum` não tem sobrecarga para tipos curtos.</span><span class="sxs-lookup"><span data-stu-id="ace3e-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="ace3e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ace3e-118">See also</span></span>

- [<span data-ttu-id="ace3e-119">Consultas agregadas</span><span class="sxs-lookup"><span data-stu-id="ace3e-119">Aggregate Queries</span></span>](aggregate-queries.md)
- <span data-ttu-id="ace3e-120">[Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="ace3e-120">[Downloading Sample Databases](downloading-sample-databases.md)</span></span>
