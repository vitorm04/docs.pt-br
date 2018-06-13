---
title: Desempenho de consultas encadeadas (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: dca2fa37a18209c5970172cb084151a58ea4ebc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336359"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="c1a8f-102">Desempenho de consultas encadeadas (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c1a8f-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="c1a8f-103">Um dos benefícios mais importantes LINQ (e LINQ to XML) é que as consultas encadeadas podem executar bem como uma única consulta maior, mais complicada.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="c1a8f-104">Uma consulta encadeada é uma consulta que usa outra consulta como sua fonte.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="c1a8f-105">Por exemplo, o seguinte código simples, `query2` tem `query1` como sua fonte:</span><span class="sxs-lookup"><span data-stu-id="c1a8f-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    new XElement("Child", 3),  
    new XElement("Child", 4)  
);  
  
var query1 = from x in root.Elements("Child")  
             where (int)x >= 3  
             select x;  
  
var query2 = from e in query1  
             where (int)e % 2 == 0  
             select e;  
  
foreach (var i in query2)  
    Console.WriteLine("{0}", (int)i);  
```  
  
 <span data-ttu-id="c1a8f-106">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="c1a8f-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="c1a8f-107">Esta consulta encadeada fornece o mesmo perfil de desempenho que iterando através de uma lista vinculada.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="c1a8f-108">O eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> tem essencialmente o mesmo desempenho que iterando através de uma lista vinculada.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="c1a8f-109"><xref:System.Xml.Linq.XContainer.Elements%2A> é implementado como um iterador com execução adiada.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="c1a8f-110">Isso significa que faz qualquer trabalho adicional a iterar através da lista vinculada, como alocar do objeto de iterador e manter controle de estado de execução.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="c1a8f-111">Este trabalho pode ser dividida em duas categorias: o trabalho que é feito no momento no iterador é configurado, e o trabalho que é feito em cada iteração.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="c1a8f-112">O trabalho de configuração é uma pequena quantidade, fixa de trabalho e o trabalho feito em cada iteração é proporcionalmente para o número de itens na coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="c1a8f-113">Em `query1`, a cláusula de `where` faz com que a consulta chama o método de <xref:System.Linq.Enumerable.Where%2A> .</span><span class="sxs-lookup"><span data-stu-id="c1a8f-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="c1a8f-114">Esse método também é implementado como um iterador.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="c1a8f-115">O trabalho de configuração consiste em criar uma instância do representante que fará referência a expressão lambda, mais a configuração normal para um iterador.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="c1a8f-116">A cada iteração, o representante é chamado para executar o predicado.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="c1a8f-117">O trabalho de configuração e trabalho feitos em cada iteração são semelhantes ao trabalho feito para iterar através do eixo.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="c1a8f-118">Em `query1`, a cláusula SELECT faz com que a consulta chama o método de <xref:System.Linq.Enumerable.Select%2A> .</span><span class="sxs-lookup"><span data-stu-id="c1a8f-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="c1a8f-119">Este método tem o mesmo perfil de desempenho que o método de <xref:System.Linq.Enumerable.Where%2A> .</span><span class="sxs-lookup"><span data-stu-id="c1a8f-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="c1a8f-120">Em `query2`, a cláusula de `where` e a cláusula `select` têm o mesmo perfil de desempenho que em `query1`.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="c1a8f-121">A interação com `query2` é portanto diretamente proporcionalmente para o número de itens na fonte da primeira consulta, ou ser uma das vezes.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="c1a8f-122">Um exemplo correspondente do Visual Basic terá o mesmo perfil de desempenho.</span><span class="sxs-lookup"><span data-stu-id="c1a8f-122">A corresponding Visual Basic example would have the same performance profile.</span></span>  
  
 <span data-ttu-id="c1a8f-123">Para obter mais informações sobre iteradores, consulte [yield](../../../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="c1a8f-123">For more information on iterators, see [yield](../../../../csharp/language-reference/keywords/yield.md).</span></span>  
  
 <span data-ttu-id="c1a8f-124">Para um tutorial mais detalhado sobre o encadeamento de consultas, consulte [Tutorial: encadear consultas juntas (C#)](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span><span class="sxs-lookup"><span data-stu-id="c1a8f-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a8f-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1a8f-125">See Also</span></span>  
 [<span data-ttu-id="c1a8f-126">Desempenho (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c1a8f-126">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
