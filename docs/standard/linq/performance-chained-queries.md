---
title: Desempenho de consultas encadeadas-LINQ to XML
description: Saiba mais sobre as consultas encadeadas que podem ser executadas, bem como uma única consulta maior e mais complicada.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: c1dae1eaf008a1f17c6884ef6b8e67d042719ad9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551909"
---
# <a name="performance-of-chained-queries-linq-to-xml"></a><span data-ttu-id="00dd3-103">Desempenho de consultas encadeadas (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="00dd3-103">Performance of chained queries (LINQ to XML)</span></span>

<span data-ttu-id="00dd3-104">Um dos benefícios mais importantes do LINQ (e LINQ to XML) é que as consultas encadeadas podem ser executadas, bem como uma única consulta que é maior e mais complicada do que as consultas encadeadas.</span><span class="sxs-lookup"><span data-stu-id="00dd3-104">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single query that is larger and more complicated than the chained queries.</span></span>

<span data-ttu-id="00dd3-105">Uma consulta encadeada é uma consulta que usa outra consulta como sua fonte.</span><span class="sxs-lookup"><span data-stu-id="00dd3-105">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="00dd3-106">Por exemplo, o seguinte código simples, `query2` tem `query1` como sua fonte:</span><span class="sxs-lookup"><span data-stu-id="00dd3-106">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

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

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="00dd3-107">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="00dd3-107">This example produces the following output:</span></span>

```output
4
```

<span data-ttu-id="00dd3-108">Esta consulta encadeada fornece o mesmo perfil de desempenho que iterando através de uma lista vinculada.</span><span class="sxs-lookup"><span data-stu-id="00dd3-108">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="00dd3-109">O eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> tem essencialmente o mesmo desempenho que iterando através de uma lista vinculada.</span><span class="sxs-lookup"><span data-stu-id="00dd3-109">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="00dd3-110"><xref:System.Xml.Linq.XContainer.Elements%2A> é implementado como um iterador com execução adiada.</span><span class="sxs-lookup"><span data-stu-id="00dd3-110"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="00dd3-111">Isso significa que faz qualquer trabalho adicional a iterar através da lista vinculada, como alocar do objeto de iterador e manter controle de estado de execução.</span><span class="sxs-lookup"><span data-stu-id="00dd3-111">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="00dd3-112">Este trabalho pode ser dividida em duas categorias: o trabalho que é feito no momento no iterador é configurado, e o trabalho que é feito em cada iteração.</span><span class="sxs-lookup"><span data-stu-id="00dd3-112">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="00dd3-113">O trabalho de configuração é uma pequena quantidade, fixa de trabalho e o trabalho feito em cada iteração é proporcionalmente para o número de itens na coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="00dd3-113">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>
- <span data-ttu-id="00dd3-114">No `query1` , a `where` cláusula ( `Where` em Visual Basic) faz com que a consulta chame o <xref:System.Linq.Enumerable.Where%2A> método.</span><span class="sxs-lookup"><span data-stu-id="00dd3-114">In `query1`, the `where` clause (`Where` in Visual Basic) causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="00dd3-115">Esse método também é implementado como um iterador.</span><span class="sxs-lookup"><span data-stu-id="00dd3-115">This method is also implemented as an iterator.</span></span> <span data-ttu-id="00dd3-116">O trabalho de configuração consiste em criar uma instância do representante que fará referência a expressão lambda, mais a configuração normal para um iterador.</span><span class="sxs-lookup"><span data-stu-id="00dd3-116">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="00dd3-117">A cada iteração, o representante é chamado para executar o predicado.</span><span class="sxs-lookup"><span data-stu-id="00dd3-117">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="00dd3-118">O trabalho de configuração e o trabalho realizado durante cada iteração são semelhantes ao trabalho feito durante a iteração por meio do eixo.</span><span class="sxs-lookup"><span data-stu-id="00dd3-118">The setup work and the work done during each iteration is similar to the work done while iterating through the axis.</span></span>
- <span data-ttu-id="00dd3-119">Em `query1`, a cláusula SELECT faz com que a consulta chama o método de <xref:System.Linq.Enumerable.Select%2A> .</span><span class="sxs-lookup"><span data-stu-id="00dd3-119">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="00dd3-120">Este método tem o mesmo perfil de desempenho que o método de <xref:System.Linq.Enumerable.Where%2A> .</span><span class="sxs-lookup"><span data-stu-id="00dd3-120">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>
- <span data-ttu-id="00dd3-121">No `query2` , a `where` cláusula ( `Where` em Visual Basic) e a `select` cláusula têm o mesmo perfil de desempenho do `query1` .</span><span class="sxs-lookup"><span data-stu-id="00dd3-121">In `query2`, both the `where` clause (`Where` in Visual Basic) and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="00dd3-122">A interação com `query2` é portanto diretamente proporcionalmente para o número de itens na fonte da primeira consulta, ou ser uma das vezes.</span><span class="sxs-lookup"><span data-stu-id="00dd3-122">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

<span data-ttu-id="00dd3-123">Para obter mais informações sobre iteradores, consulte [yield](../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="00dd3-123">For more information on iterators, see [yield](../../csharp/language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="00dd3-124">Para obter um tutorial mais detalhado sobre como encadear consultas, consulte [tutorial: encadear consultas juntas (C#)](chain-queries-example.md).</span><span class="sxs-lookup"><span data-stu-id="00dd3-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chain queries together (C#)](chain-queries-example.md).</span></span>
