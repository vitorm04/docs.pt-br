---
title: Retornar o primeiro elemento em uma sequência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: dca917b3c12b0f9923cc9ea34a2568c412a09831
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081811"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="cab91-102">Retornar o primeiro elemento em uma sequência</span><span class="sxs-lookup"><span data-stu-id="cab91-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="cab91-103">Use o operador de <xref:System.Linq.Enumerable.First%2A> para retornar o primeiro elemento em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="cab91-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="cab91-104">Consultas que usam <xref:System.Linq.Enumerable.First%2A> é executado imediatamente.</span><span class="sxs-lookup"><span data-stu-id="cab91-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="cab91-105">não oferece suporte a <xref:System.Linq.Enumerable.Last%2A> operador.</span><span class="sxs-lookup"><span data-stu-id="cab91-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cab91-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cab91-106">Example</span></span>  
 <span data-ttu-id="cab91-107">O código a seguir localiza o primeiro `Shipper` em uma tabela:</span><span class="sxs-lookup"><span data-stu-id="cab91-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="cab91-108">Se você executa essa consulta na base de dados de exemplo Northwind, os resultados são</span><span class="sxs-lookup"><span data-stu-id="cab91-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 `ID = 1, Company = Speedy Express`<span data-ttu-id="cab91-109">.</span><span class="sxs-lookup"><span data-stu-id="cab91-109">.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="cab91-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cab91-110">Example</span></span>  
 <span data-ttu-id="cab91-111">O código a seguir localiza único `Customer` que tem `CustomerID` BONAP.</span><span class="sxs-lookup"><span data-stu-id="cab91-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="cab91-112">Se você executa essa consulta na base de dados de exemplo Northwind, os resultados são `ID = BONAP, Contact = Laurence Lebihan`.</span><span class="sxs-lookup"><span data-stu-id="cab91-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="cab91-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cab91-113">See also</span></span>

- [<span data-ttu-id="cab91-114">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="cab91-114">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="cab91-115">Baixar bancos de dados de amostra</span><span class="sxs-lookup"><span data-stu-id="cab91-115">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
