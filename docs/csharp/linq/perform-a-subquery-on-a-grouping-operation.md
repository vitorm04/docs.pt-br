---
title: "Executar uma subconsulta em uma operação de agrupamento"
description: "Como executar uma subconsulta em uma operação de agrupamento."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 68acc07e0c33d042123d3cd403a73d58a7c3d245
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="a1181-104">Executar uma subconsulta em uma operação de agrupamento</span><span class="sxs-lookup"><span data-stu-id="a1181-104">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="a1181-105">Este tópico mostra duas formas diferentes de criar uma consulta que ordena os dados de origem em grupos e, então, realiza uma subconsulta em cada grupo individualmente.</span><span class="sxs-lookup"><span data-stu-id="a1181-105">This topic shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="a1181-106">A técnica básica em cada exemplo é agrupar os elementos de origem usando uma *continuação* chamada `newGroup` e, em seguida, gerar uma nova subconsulta de `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="a1181-106">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="a1181-107">Essa subconsulta é executada em cada novo grupo criado pela consulta externa.</span><span class="sxs-lookup"><span data-stu-id="a1181-107">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="a1181-108">Observe que, nesse exemplo específico, a saída final não é um grupo, mas uma sequência simples de tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="a1181-108">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
 <span data-ttu-id="a1181-109">Para obter mais informações sobre como agrupar, consulte [Cláusula group](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a1181-109">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="a1181-110">Para obter mais informações sobre continuações, consulte [into](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="a1181-110">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="a1181-111">O exemplo a seguir usa uma estrutura de dados na memória como a fonte de dados, mas os mesmos princípios se aplicam a qualquer tipo de fonte de dados do LINQ.</span><span class="sxs-lookup"><span data-stu-id="a1181-111">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1181-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1181-112">Example</span></span> 

 > [!NOTE]
 > <span data-ttu-id="a1181-113">Este exemplo contém referências a objetos que são definidos no código de exemplo em [Consultar uma coleção de objetos](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="a1181-113">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

 <span data-ttu-id="a1181-114">[!code-cs[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a1181-114">[!code-cs[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]</span></span>  
   
## <a name="see-also"></a><span data-ttu-id="a1181-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1181-115">See also</span></span>  
 [<span data-ttu-id="a1181-116">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="a1181-116">LINQ Query Expressions</span></span>](index.md)

