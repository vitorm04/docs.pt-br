---
title: Conta todas o número de elementos em uma sequência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: d983bc14f4fda04bda0a6f363db4c11f062c4c48
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164344"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="b479a-102">Conta todas o número de elementos em uma sequência</span><span class="sxs-lookup"><span data-stu-id="b479a-102">Count the Number of Elements in a Sequence</span></span>

<span data-ttu-id="b479a-103">Use o operador de <xref:System.Linq.Enumerable.Count%2A> para contar o número de elementos em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="b479a-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="b479a-104">Executando esta consulta na base de dados de exemplo Northwind gerencia uma saída de `91`.</span><span class="sxs-lookup"><span data-stu-id="b479a-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b479a-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b479a-105">Example</span></span>  

 <span data-ttu-id="b479a-106">O exemplo conta o número de `Customers` na base de dados.</span><span class="sxs-lookup"><span data-stu-id="b479a-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="b479a-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b479a-107">Example</span></span>  

 <span data-ttu-id="b479a-108">O exemplo conta o número de produtos na base de dados que não foi interrompida.</span><span class="sxs-lookup"><span data-stu-id="b479a-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="b479a-109">Executando este exemplo com o base de dados de exemplo Northwind gerencia uma saída de `69`.</span><span class="sxs-lookup"><span data-stu-id="b479a-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b479a-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="b479a-110">See also</span></span>

- [<span data-ttu-id="b479a-111">Consultas de agregação</span><span class="sxs-lookup"><span data-stu-id="b479a-111">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="b479a-112">Baixar bancos de dados de amostra</span><span class="sxs-lookup"><span data-stu-id="b479a-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
