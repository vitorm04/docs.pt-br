---
title: Desempenho de consultas encadeadas (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 8a4893a000bc80fa703e7d47aa5d73f02b95a8ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601864"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="fcabe-102">Desempenho de consultas encadeadas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcabe-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="fcabe-103">Um dos benefícios mais importantes LINQ (e LINQ to XML) é que as consultas encadeadas podem executar bem como uma única consulta maior, mais complicada.</span><span class="sxs-lookup"><span data-stu-id="fcabe-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="fcabe-104">Uma consulta encadeada é uma consulta que usa outra consulta como sua fonte.</span><span class="sxs-lookup"><span data-stu-id="fcabe-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="fcabe-105">Por exemplo, o seguinte código simples, `query2` tem `query1` como sua fonte:</span><span class="sxs-lookup"><span data-stu-id="fcabe-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
```  
  
 <span data-ttu-id="fcabe-106">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="fcabe-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="fcabe-107">Esta consulta encadeada fornece o mesmo perfil de desempenho que iterando através de uma lista vinculada.</span><span class="sxs-lookup"><span data-stu-id="fcabe-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="fcabe-108">O eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> tem essencialmente o mesmo desempenho que iterando através de uma lista vinculada.</span><span class="sxs-lookup"><span data-stu-id="fcabe-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="fcabe-109"><xref:System.Xml.Linq.XContainer.Elements%2A> é implementado como um iterador com execução adiada.</span><span class="sxs-lookup"><span data-stu-id="fcabe-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="fcabe-110">Isso significa que faz qualquer trabalho adicional a iterar através da lista vinculada, como alocar do objeto de iterador e manter controle de estado de execução.</span><span class="sxs-lookup"><span data-stu-id="fcabe-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="fcabe-111">Este trabalho pode ser dividida em duas categorias: o trabalho que é feito no momento no iterador é configurado, e o trabalho que é feito em cada iteração.</span><span class="sxs-lookup"><span data-stu-id="fcabe-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="fcabe-112">O trabalho de configuração é uma pequena quantidade, fixa de trabalho e o trabalho feito em cada iteração é proporcionalmente para o número de itens na coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="fcabe-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="fcabe-113">Em `query1`, a cláusula de `Where` faz com que a consulta chama o método de <xref:System.Linq.Enumerable.Where%2A> .</span><span class="sxs-lookup"><span data-stu-id="fcabe-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="fcabe-114">Esse método também é implementado como um iterador.</span><span class="sxs-lookup"><span data-stu-id="fcabe-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="fcabe-115">O trabalho de configuração consiste em criar uma instância do representante que fará referência a expressão lambda, mais a configuração normal para um iterador.</span><span class="sxs-lookup"><span data-stu-id="fcabe-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="fcabe-116">A cada iteração, o representante é chamado para executar o predicado.</span><span class="sxs-lookup"><span data-stu-id="fcabe-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="fcabe-117">O trabalho de configuração e trabalho feitos em cada iteração são semelhantes ao trabalho feito para iterar através do eixo.</span><span class="sxs-lookup"><span data-stu-id="fcabe-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="fcabe-118">Em `query1`, a cláusula SELECT faz com que a consulta chama o método de <xref:System.Linq.Enumerable.Select%2A> .</span><span class="sxs-lookup"><span data-stu-id="fcabe-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="fcabe-119">Este método tem o mesmo perfil de desempenho que o método de <xref:System.Linq.Enumerable.Where%2A> .</span><span class="sxs-lookup"><span data-stu-id="fcabe-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="fcabe-120">Em `query2`, a cláusula de `Where` e a cláusula `Select` têm o mesmo perfil de desempenho que em `query1`.</span><span class="sxs-lookup"><span data-stu-id="fcabe-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="fcabe-121">A interação com `query2` é portanto diretamente proporcionalmente para o número de itens na fonte da primeira consulta, ou ser uma das vezes.</span><span class="sxs-lookup"><span data-stu-id="fcabe-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcabe-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcabe-122">See also</span></span>
- [<span data-ttu-id="fcabe-123">Desempenho (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcabe-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
