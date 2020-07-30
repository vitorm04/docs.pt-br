---
title: Consultas estaticamente compiladas (LINQ to XML) (C#)
description: Saiba mais sobre consultas compiladas estaticamente em LINQ to XML em C# e como elas diferem das consultas XPath, que devem ser interpretadas em tempo de execução.
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: cd2e6a6507311d5fc17215a22c70bd0449292b6f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302302"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="1e4d3-103">Consultas estaticamente compiladas (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1e4d3-103">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="1e4d3-104">Um de desempenho mais importante beneficia LINQ to XML, diferentemente de <xref:System.Xml.XmlDocument>, é que as consultas em LINQ to XML são compiladas estaticamente, enquanto as consultas XPath devem ser interpretado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-104">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="1e4d3-105">Esse recurso é interna a LINQ to XML, portanto você não precisa executar etapas adicionais para aproveitá-lo, mas é útil entender a diferença ao escolher entre as duas tecnologias.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-105">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="1e4d3-106">Este tópico explica a diferença.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-106">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="1e4d3-107">Consultas compiladas estaticamente versus XPath</span><span class="sxs-lookup"><span data-stu-id="1e4d3-107">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="1e4d3-108">O exemplo a seguir mostra como obter os elementos descendentes com um nome especificado e, com um atributo com um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-108">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="1e4d3-109">A seguir está a expressão XPath equivalente:`//Address[@Type='Shipping']`</span><span class="sxs-lookup"><span data-stu-id="1e4d3-109">The following is the equivalent XPath expression: `//Address[@Type='Shipping']`</span></span>
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="1e4d3-110">A expressão de consulta nesse exemplo é reescrita pelo compilador a sintaxe da consulta com base em método.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-110">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="1e4d3-111">O exemplo a seguir, que é escrito na sintaxe da consulta com base em método, gerenciar os mesmos resultados que anterior:</span><span class="sxs-lookup"><span data-stu-id="1e4d3-111">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="1e4d3-112">O método de <xref:System.Linq.Enumerable.Where%2A> é um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-112">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="1e4d3-113">Para obter mais informações, consulte [Métodos de extensão](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="1e4d3-113">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="1e4d3-114">Porque <xref:System.Linq.Enumerable.Where%2A> é um método de extensão, a consulta anterior é criada como se ele foi gravado como segue:</span><span class="sxs-lookup"><span data-stu-id="1e4d3-114">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="1e4d3-115">Este exemplo gerencia exatamente os mesmos resultados que os dois exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-115">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="1e4d3-116">Isso ilustra o fato de que as consultas são compiladas efetivamente estaticamente associados em chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-116">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="1e4d3-117">Isso, combinado com a semântica de execução adiada de iteradores, melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-117">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="1e4d3-118">Para obter mais informações sobre a semântica de execução adiada dos iteradores, consulte [Execução adiada e avaliação lenta em LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1e4d3-118">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e4d3-119">Esses exemplos são representante de código que o compilador pode escrever.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-119">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="1e4d3-120">A implementação real pode diferir um pouco desses exemplos, mas o desempenho será o mesmo ou semelhante a esses exemplos.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-120">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="1e4d3-121">Executando com expressões XPath XmlDocument</span><span class="sxs-lookup"><span data-stu-id="1e4d3-121">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="1e4d3-122">O exemplo a seguir usa <xref:System.Xml.XmlDocument> para executar os mesmos resultados que os exemplos anteriores:</span><span class="sxs-lookup"><span data-stu-id="1e4d3-122">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="1e4d3-123">Esta consulta retorna as mesmas saída que os exemplos que usam LINQ to XML; a única diferença é que LINQ to XML recua XML impresso, enquanto <xref:System.Xml.XmlDocument> não.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-123">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="1e4d3-124">No entanto, a abordagem de <xref:System.Xml.XmlDocument> geralmente não executa bem como LINQ to XML, porque o método de <xref:System.Xml.XmlNode.SelectNodes%2A> deve fazer o seguinte internamente todas as vezes nele é chamado:</span><span class="sxs-lookup"><span data-stu-id="1e4d3-124">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="1e4d3-125">Analisa a cadeia de caracteres que contém a expressão XPath, quebrando a cadeia de caracteres em tokens.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-125">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="1e4d3-126">Valida os tokens para certificar-se de que a expressão XPath é válido.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-126">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="1e4d3-127">Converte a expressão em uma árvore de expressão interna.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-127">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="1e4d3-128">Itera através de nós, selecionando adequadamente os nós para o conjunto de resultados com base na avaliação da expressão.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-128">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="1e4d3-129">Este é significativamente mais do que o trabalho feito pela consulta correspondente LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-129">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="1e4d3-130">A diferença desempenho específico variam para tipos diferentes de consultas, mas em geral LINQ to XML consultas menos trabalho e, portanto, executam melhor do que as expressões XPath de avaliação usando <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-130">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
