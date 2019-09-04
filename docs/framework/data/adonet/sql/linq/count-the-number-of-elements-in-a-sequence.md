---
title: Conta todas o número de elementos em uma sequência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 74e24aeb64b0097cba3975e76475034e6bb9544d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247702"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="aa4cf-102">Conta todas o número de elementos em uma sequência</span><span class="sxs-lookup"><span data-stu-id="aa4cf-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="aa4cf-103">Use o operador de <xref:System.Linq.Enumerable.Count%2A> para contar o número de elementos em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="aa4cf-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="aa4cf-104">Executando esta consulta na base de dados de exemplo Northwind gerencia uma saída de `91`.</span><span class="sxs-lookup"><span data-stu-id="aa4cf-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa4cf-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa4cf-105">Example</span></span>  
 <span data-ttu-id="aa4cf-106">O exemplo conta o número de `Customers` na base de dados.</span><span class="sxs-lookup"><span data-stu-id="aa4cf-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="aa4cf-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa4cf-107">Example</span></span>  
 <span data-ttu-id="aa4cf-108">O exemplo conta o número de produtos na base de dados que não foi interrompida.</span><span class="sxs-lookup"><span data-stu-id="aa4cf-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="aa4cf-109">Executando este exemplo com o base de dados de exemplo Northwind gerencia uma saída de `69`.</span><span class="sxs-lookup"><span data-stu-id="aa4cf-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="aa4cf-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa4cf-110">See also</span></span>

- [<span data-ttu-id="aa4cf-111">Consultas agregadas</span><span class="sxs-lookup"><span data-stu-id="aa4cf-111">Aggregate Queries</span></span>](aggregate-queries.md)
- <span data-ttu-id="aa4cf-112">[Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="aa4cf-112">[Downloading Sample Databases](downloading-sample-databases.md)</span></span>
