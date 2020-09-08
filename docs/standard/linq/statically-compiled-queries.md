---
title: Consultas compiladas estaticamente-LINQ to XML
description: Saiba como LINQ to XML consultas obtenha uma vantagem de desempenho sobre o XMLDocument, sendo compilado estaticamente.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 53dd47247eae8802dcf8187d0e82eb1c8bead9f9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551998"
---
# <a name="statically-compiled-queries-linq-to-xml"></a><span data-ttu-id="7bd4f-103">Consultas compiladas estaticamente (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7bd4f-103">Statically compiled queries (LINQ to XML)</span></span>

<span data-ttu-id="7bd4f-104">Uma das vantagens de desempenho mais importantes do LINQ to XML, em comparação com o <xref:System.Xml.XmlDocument> , é que as consultas no LINQ to XML são compiladas estaticamente, enquanto as consultas XPath devem ser interpretadas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-104">One of the most important performance advantages of LINQ to XML, as compared to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="7bd4f-105">Esse recurso é criado em LINQ to XML, de modo que você não precisa executar etapas adicionais para aproveitar isso, mas é útil entender a distinção ao escolher entre as duas tecnologias.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-105">This feature is built into LINQ to XML, so you don't have to perform extra steps to take advantage of it, but it's helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="7bd4f-106">Este artigo explica a diferença.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-106">This article explains the difference.</span></span>

## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="7bd4f-107">Consultas compiladas estaticamente versus XPath</span><span class="sxs-lookup"><span data-stu-id="7bd4f-107">Statically compiled queries vs. XPath</span></span>

<span data-ttu-id="7bd4f-108">O exemplo a seguir mostra como obter os elementos descendentes com um nome especificado e, com um atributo com um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-108">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span> <span data-ttu-id="7bd4f-109">A expressão XPath equivalente é `//Address[@Type='Shipping']` .</span><span class="sxs-lookup"><span data-stu-id="7bd4f-109">The equivalent XPath expression is `//Address[@Type='Shipping']`.</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    from el in po.Descendants("Address")
    where (string)el.Attribute("Type") == "Shipping"
    select el;

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="7bd4f-110">A expressão de consulta neste exemplo é reescrita pelo compilador para sintaxe de consulta baseada em método.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-110">The query expression in this example is rewritten by the compiler to method-based query syntax.</span></span> <span data-ttu-id="7bd4f-111">O exemplo a seguir, que é escrito na sintaxe da consulta com base em método, gerenciar os mesmos resultados que anterior:</span><span class="sxs-lookup"><span data-stu-id="7bd4f-111">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    po
    .Descendants("Address")
    .Where(el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

 ```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="7bd4f-112">O método de <xref:System.Linq.Enumerable.Where%2A> é um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-112">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="7bd4f-113">Para obter mais informações, consulte [métodos de extensão (guia de programação C#)](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="7bd4f-113">For more information, see [Extension Methods (C# Programming Guide)](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="7bd4f-114">Porque <xref:System.Linq.Enumerable.Where%2A> é um método de extensão, a consulta anterior é criada como se ele foi gravado como segue:</span><span class="sxs-lookup"><span data-stu-id="7bd4f-114">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    System.Linq.Enumerable.Where(
        po.Descendants("Address"),
        el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="7bd4f-115">Este exemplo gerencia exatamente os mesmos resultados que os dois exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-115">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="7bd4f-116">Isso ilustra o fato de que as consultas são compiladas efetivamente estaticamente associados em chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-116">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="7bd4f-117">Isso, combinado com a semântica de execução adiada de iteradores, melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-117">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="7bd4f-118">Para obter mais informações sobre a semântica de execução adiada de iteradores, consulte [execução retardada e avaliação lenta](deferred-execution-lazy-evaluation.md).</span><span class="sxs-lookup"><span data-stu-id="7bd4f-118">For more information about the deferred execution semantics of iterators, see [Deferred execution and lazy evaluation](deferred-execution-lazy-evaluation.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7bd4f-119">Esses exemplos são representante de código que o compilador pode escrever.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-119">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="7bd4f-120">A implementação real pode ser ligeiramente diferente desses exemplos, mas o desempenho será o mesmo que, ou semelhante, a esses exemplos.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-120">The actual implementation might differ slightly from these examples, but the performance will be the same as, or similar to, these examples.</span></span>

## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="7bd4f-121">Executando expressões XPath com XmlDocument</span><span class="sxs-lookup"><span data-stu-id="7bd4f-121">Executing XPath expressions with XmlDocument</span></span>

<span data-ttu-id="7bd4f-122">O exemplo a seguir usa <xref:System.Xml.XmlDocument> para executar os mesmos resultados que os exemplos anteriores:</span><span class="sxs-lookup"><span data-stu-id="7bd4f-122">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>

```csharp
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");
XmlDocument doc = new XmlDocument();
doc.Load(reader);
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");
foreach (XmlNode n in nl)
    Console.WriteLine(n.OuterXml);
reader.Close();
```

```vb
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")
Dim doc As New Xml.XmlDocument()
doc.Load(reader)
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")
For Each n As Xml.XmlNode In nl
    Console.WriteLine(n.OuterXml)
Next
reader.Close()
```

<span data-ttu-id="7bd4f-123">Essa consulta retorna a mesma saída que os exemplos que usam LINQ to XML; a única diferença é que LINQ to XML recua o XML impresso, enquanto <xref:System.Xml.XmlDocument> não.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-123">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> doesn't.</span></span>

<span data-ttu-id="7bd4f-124">No entanto, a <xref:System.Xml.XmlDocument> abordagem geralmente não é executada, bem como LINQ to XML, porque o <xref:System.Xml.XmlNode.SelectNodes%2A> método deve fazer o seguinte sempre que for chamado:</span><span class="sxs-lookup"><span data-stu-id="7bd4f-124">However, the <xref:System.Xml.XmlDocument> approach generally doesn't perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following every time it's called:</span></span>

- <span data-ttu-id="7bd4f-125">Analise a cadeia de caracteres que contém a expressão XPath, dividindo a cadeia de caracteres em tokens.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-125">Parse the string that contains the XPath expression, breaking the string into tokens.</span></span>
- <span data-ttu-id="7bd4f-126">Valide os tokens para certificar-se de que a expressão XPath é válida.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-126">Validate the tokens to make sure that the XPath expression is valid.</span></span>
- <span data-ttu-id="7bd4f-127">Traduza a expressão em uma árvore de expressão interna.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-127">Translate the expression into an internal expression tree.</span></span>
- <span data-ttu-id="7bd4f-128">Itere os nós, selecionando adequadamente os nós para o conjunto de resultados com base na avaliação da expressão.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-128">Iterate through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>

<span data-ttu-id="7bd4f-129">Este é significativamente mais do que o trabalho feito pela consulta correspondente LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-129">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="7bd4f-130">A diferença desempenho específico variam para tipos diferentes de consultas, mas em geral LINQ to XML consultas menos trabalho e, portanto, executam melhor do que as expressões XPath de avaliação usando <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="7bd4f-130">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>
