---
title: "Localizar o valor mínimo em uma sequência numérica"
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
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9cc16b09912cb9cc695fc350d9fd4530ea99e794
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="5c6fd-102">Localizar o valor mínimo em uma sequência numérica</span><span class="sxs-lookup"><span data-stu-id="5c6fd-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="5c6fd-103">Use o operador de <xref:System.Linq.Enumerable.Min%2A> para retornar o valor mínimo de uma sequência de valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="5c6fd-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c6fd-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c6fd-104">Example</span></span>  
 <span data-ttu-id="5c6fd-105">O exemplo a seguir localiza o menor preço unitário de qualquer produto.</span><span class="sxs-lookup"><span data-stu-id="5c6fd-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="5c6fd-106">Se você executar essa consulta no banco de dados de exemplo do Northwind, a saída será: `2.5000`.</span><span class="sxs-lookup"><span data-stu-id="5c6fd-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="5c6fd-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c6fd-107">Example</span></span>  
 <span data-ttu-id="5c6fd-108">O exemplo a seguir localiza a menor quantidade de frete para qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="5c6fd-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="5c6fd-109">Se você executar essa consulta no banco de dados de exemplo do Northwind, a saída será: `0.0200`.</span><span class="sxs-lookup"><span data-stu-id="5c6fd-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="5c6fd-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c6fd-110">Example</span></span>  
 <span data-ttu-id="5c6fd-111">Os seguintes o exemplo usa mínimos para localizar `Products` que têm o menor preço unitário em cada categoria.</span><span class="sxs-lookup"><span data-stu-id="5c6fd-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="5c6fd-112">A saída são organizadas por categoria.</span><span class="sxs-lookup"><span data-stu-id="5c6fd-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="5c6fd-113">Se você executa a consulta anterior com o base de dados de exemplo Northwind, resultados assemelhar-se-ão o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5c6fd-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="5c6fd-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c6fd-114">See Also</span></span>  
 [<span data-ttu-id="5c6fd-115">Consultas agregadas</span><span class="sxs-lookup"><span data-stu-id="5c6fd-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="5c6fd-116">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="5c6fd-116">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)</span></span>
