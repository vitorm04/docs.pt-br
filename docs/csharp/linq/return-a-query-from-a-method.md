---
title: Retornar uma consulta de um método
description: Como retornar uma consulta.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1c5fa534f3f39f8201d93b986e687d85bb303736
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510781"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="5506c-103">Como retornar uma consulta de um método (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="5506c-103">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="5506c-104">Este exemplo mostra como retornar uma consulta de um método como o valor retornado e como um parâmetro `out`.</span><span class="sxs-lookup"><span data-stu-id="5506c-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="5506c-105">Os objetos de consulta são combináveis, o que significa que você pode retornar uma consulta de um método.</span><span class="sxs-lookup"><span data-stu-id="5506c-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="5506c-106">Os objetos que representam consultas não armazenam a coleção resultante, mas as etapas para gerar os resultados quando necessário.</span><span class="sxs-lookup"><span data-stu-id="5506c-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="5506c-107">A vantagem de retornar objetos de consulta de métodos é que eles podem ser ainda mais modificados e combinados.</span><span class="sxs-lookup"><span data-stu-id="5506c-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="5506c-108">Portanto, qualquer valor retornado ou parâmetro `out` de um método que retorna uma consulta também deve ter o tipo.</span><span class="sxs-lookup"><span data-stu-id="5506c-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="5506c-109">Se um método materializa uma consulta em um tipo <xref:System.Collections.Generic.List%601> ou <xref:System.Array> concreto, considera-se que ele está retornando os resultados da consulta em vez da consulta em si.</span><span class="sxs-lookup"><span data-stu-id="5506c-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="5506c-110">Uma variável de consulta retornada de um método ainda pode ser combinada ou modificada.</span><span class="sxs-lookup"><span data-stu-id="5506c-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5506c-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5506c-111">Example</span></span>  
 <span data-ttu-id="5506c-112">No exemplo a seguir, o primeiro método retorna uma consulta como um valor retornado e o segundo método retorna uma consulta como um parâmetro `out`.</span><span class="sxs-lookup"><span data-stu-id="5506c-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="5506c-113">Observe que em ambos os casos é uma consulta que é retornada, não os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="5506c-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="5506c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5506c-114">See Also</span></span>

- [<span data-ttu-id="5506c-115">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="5506c-115">Language Integrated Query (LINQ)</span></span>](index.md)
