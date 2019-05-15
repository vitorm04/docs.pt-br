---
title: Desempenho de consultas encadeadas (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: da01901a8c4208965a339cb3cf446f054f65638b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596844"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="311e7-102">Desempenho de consultas encadeadas (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="311e7-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="311e7-103">Um dos benefícios mais importantes LINQ (e LINQ to XML) é que as consultas encadeadas podem executar bem como uma única consulta maior, mais complicada.</span><span class="sxs-lookup"><span data-stu-id="311e7-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="311e7-104">Uma consulta encadeada é uma consulta que usa outra consulta como sua fonte.</span><span class="sxs-lookup"><span data-stu-id="311e7-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="311e7-105">Por exemplo, o seguinte código simples, `query2` tem `query1` como sua fonte:</span><span class="sxs-lookup"><span data-stu-id="311e7-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
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
  
 <span data-ttu-id="311e7-106">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="311e7-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="311e7-107">Esta consulta encadeada fornece o mesmo perfil de desempenho que iterando através de uma lista vinculada.</span><span class="sxs-lookup"><span data-stu-id="311e7-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
- <span data-ttu-id="311e7-108">O eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> tem essencialmente o mesmo desempenho que iterando através de uma lista vinculada.</span><span class="sxs-lookup"><span data-stu-id="311e7-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="311e7-109"><xref:System.Xml.Linq.XContainer.Elements%2A> é implementado como um iterador com execução adiada.</span><span class="sxs-lookup"><span data-stu-id="311e7-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="311e7-110">Isso significa que faz qualquer trabalho adicional a iterar através da lista vinculada, como alocar do objeto de iterador e manter controle de estado de execução.</span><span class="sxs-lookup"><span data-stu-id="311e7-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="311e7-111">Este trabalho pode ser dividida em duas categorias: o trabalho que é feito no momento no iterador é configurado, e o trabalho que é feito em cada iteração.</span><span class="sxs-lookup"><span data-stu-id="311e7-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="311e7-112">O trabalho de configuração é uma pequena quantidade, fixa de trabalho e o trabalho feito em cada iteração é proporcionalmente para o número de itens na coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="311e7-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
- <span data-ttu-id="311e7-113">Em `query1`, a cláusula de `where` faz com que a consulta chama o método de <xref:System.Linq.Enumerable.Where%2A> .</span><span class="sxs-lookup"><span data-stu-id="311e7-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="311e7-114">Esse método também é implementado como um iterador.</span><span class="sxs-lookup"><span data-stu-id="311e7-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="311e7-115">O trabalho de configuração consiste em criar uma instância do representante que fará referência a expressão lambda, mais a configuração normal para um iterador.</span><span class="sxs-lookup"><span data-stu-id="311e7-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="311e7-116">A cada iteração, o representante é chamado para executar o predicado.</span><span class="sxs-lookup"><span data-stu-id="311e7-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="311e7-117">O trabalho de configuração e trabalho feitos em cada iteração são semelhantes ao trabalho feito para iterar através do eixo.</span><span class="sxs-lookup"><span data-stu-id="311e7-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
- <span data-ttu-id="311e7-118">Em `query1`, a cláusula SELECT faz com que a consulta chama o método de <xref:System.Linq.Enumerable.Select%2A> .</span><span class="sxs-lookup"><span data-stu-id="311e7-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="311e7-119">Este método tem o mesmo perfil de desempenho que o método de <xref:System.Linq.Enumerable.Where%2A> .</span><span class="sxs-lookup"><span data-stu-id="311e7-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
- <span data-ttu-id="311e7-120">Em `query2`, a cláusula de `where` e a cláusula `select` têm o mesmo perfil de desempenho que em `query1`.</span><span class="sxs-lookup"><span data-stu-id="311e7-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="311e7-121">A interação com `query2` é portanto diretamente proporcionalmente para o número de itens na fonte da primeira consulta, ou ser uma das vezes.</span><span class="sxs-lookup"><span data-stu-id="311e7-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="311e7-122">Um exemplo correspondente do Visual Basic terá o mesmo perfil de desempenho.</span><span class="sxs-lookup"><span data-stu-id="311e7-122">A corresponding Visual Basic example would have the same performance profile.</span></span>  
  
 <span data-ttu-id="311e7-123">Para obter mais informações sobre iteradores, consulte [yield](../../../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="311e7-123">For more information on iterators, see [yield](../../../../csharp/language-reference/keywords/yield.md).</span></span>  
  
 <span data-ttu-id="311e7-124">Para obter um tutorial mais detalhado sobre o encadeamento de consultas, confira [Tutorial: Encadeando consultas](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span><span class="sxs-lookup"><span data-stu-id="311e7-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311e7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="311e7-125">See also</span></span>

- [<span data-ttu-id="311e7-126">Desempenho (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="311e7-126">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
