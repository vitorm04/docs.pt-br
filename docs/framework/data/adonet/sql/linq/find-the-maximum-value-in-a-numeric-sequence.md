---
title: "Localizar o valor máximo em uma sequência numérica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 387fe8db55da337b970bbac0e6e046b43433b482
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="4d668-102">Localizar o valor máximo em uma sequência numérica</span><span class="sxs-lookup"><span data-stu-id="4d668-102">Find the Maximum Value in a Numeric Sequence</span></span>
<span data-ttu-id="4d668-103">Use o operador de <xref:System.Linq.Enumerable.Max%2A> para localizar o valor mais alto em uma sequência de valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="4d668-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d668-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d668-104">Example</span></span>  
 <span data-ttu-id="4d668-105">O exemplo a seguir localiza a última data de aluguer para qualquer funcionários.</span><span class="sxs-lookup"><span data-stu-id="4d668-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="4d668-106">Se você executa essa consulta na base de dados de exemplo Northwind, a saída são: `11/15/1994 12:00:00 AM`.</span><span class="sxs-lookup"><span data-stu-id="4d668-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="4d668-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d668-107">Example</span></span>  
 <span data-ttu-id="4d668-108">O exemplo a seguir localiza a maioria de unidades em estoque para qualquer produto.</span><span class="sxs-lookup"><span data-stu-id="4d668-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="4d668-109">Se você executa esse exemplo com o base de dados de exemplo Northwind, a saída são: `125`.</span><span class="sxs-lookup"><span data-stu-id="4d668-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="4d668-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d668-110">Example</span></span>  
 <span data-ttu-id="4d668-111">Os seguintes o exemplo usa máximo para localizar `Products` que têm o preço unitário o maior em cada categoria.</span><span class="sxs-lookup"><span data-stu-id="4d668-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="4d668-112">A saída listam os resultados por categoria.</span><span class="sxs-lookup"><span data-stu-id="4d668-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="4d668-113">Se você executa a consulta anterior com o base de dados de exemplo Northwind, resultados assemelhar-se-ão o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4d668-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="4d668-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d668-114">See Also</span></span>  
 [<span data-ttu-id="4d668-115">Consultas agregadas</span><span class="sxs-lookup"><span data-stu-id="4d668-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="4d668-116">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="4d668-116">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)</span></span>
