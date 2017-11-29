---
title: "Retornar uma consulta de um método"
description: Como retornar uma consulta.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: c1b69e3f5f0cd2c50ae80d2454e6b7f13dc30344
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="65a43-104">Como retornar uma consulta de um método (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="65a43-104">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="65a43-105">Este exemplo mostra como retornar uma consulta de um método como o valor retornado e como um parâmetro `out`.</span><span class="sxs-lookup"><span data-stu-id="65a43-105">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="65a43-106">Os objetos de consulta são combináveis, o que significa que você pode retornar uma consulta de um método.</span><span class="sxs-lookup"><span data-stu-id="65a43-106">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="65a43-107">Os objetos que representam consultas não armazenam a coleção resultante, mas as etapas para gerar os resultados quando necessário.</span><span class="sxs-lookup"><span data-stu-id="65a43-107">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="65a43-108">A vantagem de retornar objetos de consulta de métodos é que eles podem ser ainda mais modificados e combinados.</span><span class="sxs-lookup"><span data-stu-id="65a43-108">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="65a43-109">Portanto, qualquer valor retornado ou parâmetro `out` de um método que retorna uma consulta também deve ter o tipo.</span><span class="sxs-lookup"><span data-stu-id="65a43-109">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="65a43-110">Se um método materializa uma consulta em um tipo <xref:System.Collections.Generic.List%601> ou <xref:System.Array> concreto, considera-se que ele está retornando os resultados da consulta em vez da consulta em si.</span><span class="sxs-lookup"><span data-stu-id="65a43-110">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="65a43-111">Uma variável de consulta retornada de um método ainda pode ser combinada ou modificada.</span><span class="sxs-lookup"><span data-stu-id="65a43-111">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65a43-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65a43-112">Example</span></span>  
 <span data-ttu-id="65a43-113">No exemplo a seguir, o primeiro método retorna uma consulta como um valor retornado e o segundo método retorna uma consulta como um parâmetro `out`.</span><span class="sxs-lookup"><span data-stu-id="65a43-113">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="65a43-114">Observe que em ambos os casos é uma consulta que é retornada, não os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="65a43-114">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="65a43-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65a43-115">See Also</span></span>  
 [<span data-ttu-id="65a43-116">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="65a43-116">LINQ Query Expressions</span></span>](index.md)
