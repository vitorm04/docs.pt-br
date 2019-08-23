---
title: Retornar o primeiro elemento em uma sequência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 39cf9270b08fce64590fef418bb428c5a781b0e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963805"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="e4c2f-102">Retornar o primeiro elemento em uma sequência</span><span class="sxs-lookup"><span data-stu-id="e4c2f-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="e4c2f-103">Use o operador de <xref:System.Linq.Enumerable.First%2A> para retornar o primeiro elemento em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="e4c2f-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="e4c2f-104">Consultas que usam <xref:System.Linq.Enumerable.First%2A> é executado imediatamente.</span><span class="sxs-lookup"><span data-stu-id="e4c2f-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e4c2f-105">não suporta o operador de <xref:System.Linq.Enumerable.Last%2A> .</span><span class="sxs-lookup"><span data-stu-id="e4c2f-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4c2f-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e4c2f-106">Example</span></span>  
 <span data-ttu-id="e4c2f-107">O código a seguir localiza o primeiro `Shipper` em uma tabela:</span><span class="sxs-lookup"><span data-stu-id="e4c2f-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="e4c2f-108">Se você executa essa consulta na base de dados de exemplo Northwind, os resultados são</span><span class="sxs-lookup"><span data-stu-id="e4c2f-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="e4c2f-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="e4c2f-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="e4c2f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e4c2f-110">Example</span></span>  
 <span data-ttu-id="e4c2f-111">O código a seguir localiza único `Customer` que tem `CustomerID` BONAP.</span><span class="sxs-lookup"><span data-stu-id="e4c2f-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="e4c2f-112">Se você executa essa consulta na base de dados de exemplo Northwind, os resultados são `ID = BONAP, Contact = Laurence Lebihan`.</span><span class="sxs-lookup"><span data-stu-id="e4c2f-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="e4c2f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4c2f-113">See also</span></span>

- [<span data-ttu-id="e4c2f-114">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="e4c2f-114">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- <span data-ttu-id="e4c2f-115">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="e4c2f-115">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)</span></span>
