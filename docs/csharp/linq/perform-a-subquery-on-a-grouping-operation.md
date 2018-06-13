---
title: Executar uma subconsulta em uma operação de agrupamento
description: Como executar uma subconsulta em uma operação de agrupamento.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 209d05c2fe8719fa9116061d199272366146f465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277323"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="587c4-103">Executar uma subconsulta em uma operação de agrupamento</span><span class="sxs-lookup"><span data-stu-id="587c4-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="587c4-104">Este tópico mostra duas formas diferentes de criar uma consulta que ordena os dados de origem em grupos e, então, realiza uma subconsulta em cada grupo individualmente.</span><span class="sxs-lookup"><span data-stu-id="587c4-104">This topic shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="587c4-105">A técnica básica em cada exemplo é agrupar os elementos de origem usando uma *continuação* chamada `newGroup` e, em seguida, gerar uma nova subconsulta de `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="587c4-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="587c4-106">Essa subconsulta é executada em cada novo grupo criado pela consulta externa.</span><span class="sxs-lookup"><span data-stu-id="587c4-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="587c4-107">Observe que, nesse exemplo específico, a saída final não é um grupo, mas uma sequência simples de tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="587c4-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
 <span data-ttu-id="587c4-108">Para obter mais informações sobre como agrupar, consulte [Cláusula group](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="587c4-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="587c4-109">Para obter mais informações sobre continuações, consulte [into](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="587c4-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="587c4-110">O exemplo a seguir usa uma estrutura de dados na memória como a fonte de dados, mas os mesmos princípios se aplicam a qualquer tipo de fonte de dados do LINQ.</span><span class="sxs-lookup"><span data-stu-id="587c4-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="587c4-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="587c4-111">Example</span></span> 

 > [!NOTE]
 > <span data-ttu-id="587c4-112">Este exemplo contém referências a objetos que são definidos no código de exemplo em [Consultar uma coleção de objetos](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="587c4-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a><span data-ttu-id="587c4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="587c4-113">See also</span></span>  
 [<span data-ttu-id="587c4-114">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="587c4-114">LINQ Query Expressions</span></span>](index.md)
