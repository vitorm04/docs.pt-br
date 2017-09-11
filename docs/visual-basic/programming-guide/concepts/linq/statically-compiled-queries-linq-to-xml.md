---
title: Compilado estaticamente consultas (LINQ to XML) (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 83d6e37a00477cedc4a5a4c520ad79ff764d5ff7
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017


---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="82ea0-102">Compilado estaticamente consultas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82ea0-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="82ea0-103">Um desempenho mais importante beneficia LINQ to XML, em vez de <xref:System.Xml.XmlDocument>, é que consultas no LINQ to XML são compiladas estaticamente, enquanto as consultas XPath devem ser interpretadas em tempo de execução.</xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="82ea0-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="82ea0-104">Esse recurso é interna a LINQ to XML, portanto você não precisa executar etapas adicionais para aproveitá-lo, mas é útil entender a diferença ao escolher entre as duas tecnologias.</span><span class="sxs-lookup"><span data-stu-id="82ea0-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="82ea0-105">Este tópico explica a diferença.</span><span class="sxs-lookup"><span data-stu-id="82ea0-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="82ea0-106">Consultas estaticamente compilado contra. XPath</span><span class="sxs-lookup"><span data-stu-id="82ea0-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="82ea0-107">O exemplo a seguir mostra como obter os elementos descendentes com um nome especificado e, com um atributo com um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="82ea0-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="82ea0-108">O seguinte é a expressão XPath equivalente:</span><span class="sxs-lookup"><span data-stu-id="82ea0-108">The following is the equivalent XPath expression:</span></span>  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="82ea0-109">A expressão de consulta nesse exemplo é reescrita pelo compilador a sintaxe da consulta com base em método.</span><span class="sxs-lookup"><span data-stu-id="82ea0-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="82ea0-110">O exemplo a seguir, que é escrito na sintaxe da consulta com base em método, gerenciar os mesmos resultados que anterior:</span><span class="sxs-lookup"><span data-stu-id="82ea0-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <span data-ttu-id="82ea0-111">O <xref:System.Linq.Enumerable.Where%2A>método é um método de extensão.</xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="82ea0-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="82ea0-112">Para obter mais informações, consulte [métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="82ea0-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="82ea0-113">Porque <xref:System.Linq.Enumerable.Where%2A>é um método de extensão, a consulta acima é compilada como se tivesse sido feita da seguinte maneira:</xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="82ea0-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="82ea0-114">Este exemplo gerencia exatamente os mesmos resultados que os dois exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="82ea0-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="82ea0-115">Isso ilustra o fato de que as consultas são compiladas efetivamente estaticamente associados em chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="82ea0-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="82ea0-116">Isso, combinado com a semântica de execução adiada de iteradores, melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="82ea0-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="82ea0-117">Para obter mais informações sobre a semântica de execução adiada de iteradores, consulte [execução adiada e avaliação lenta em LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="82ea0-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82ea0-118">Esses exemplos são representante de código que o compilador pode escrever.</span><span class="sxs-lookup"><span data-stu-id="82ea0-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="82ea0-119">A implementação real pode diferir um pouco desses exemplos, mas o desempenho será o mesmo ou semelhante a esses exemplos.</span><span class="sxs-lookup"><span data-stu-id="82ea0-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="82ea0-120">Executando com expressões XPath XmlDocument</span><span class="sxs-lookup"><span data-stu-id="82ea0-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="82ea0-121">O exemplo a seguir usa <xref:System.Xml.XmlDocument>para alcançar os mesmos resultados que os exemplos anteriores:</xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="82ea0-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
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
  
 <span data-ttu-id="82ea0-122">Esta consulta retorna o mesmo resultado que os exemplos que usam LINQ para XML; a única diferença é que o LINQ to XML recua XML impresso, enquanto <xref:System.Xml.XmlDocument>não.</xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="82ea0-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="82ea0-123">No entanto, o <xref:System.Xml.XmlDocument>abordagem geralmente não executam bem como o LINQ to XML, porque o <xref:System.Xml.XmlNode.SelectNodes%2A>método deve fazer o seguinte internamente toda vez que ele é chamado:</xref:System.Xml.XmlNode.SelectNodes%2A> </xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="82ea0-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
-   <span data-ttu-id="82ea0-124">Analisa a cadeia de caracteres que contém a expressão XPath, quebrando a cadeia de caracteres em tokens.</span><span class="sxs-lookup"><span data-stu-id="82ea0-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
-   <span data-ttu-id="82ea0-125">Valida os tokens para certificar-se de que a expressão XPath é válido.</span><span class="sxs-lookup"><span data-stu-id="82ea0-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
-   <span data-ttu-id="82ea0-126">Converte a expressão em uma árvore de expressão interna.</span><span class="sxs-lookup"><span data-stu-id="82ea0-126">It translates the expression into an internal expression tree.</span></span>  
  
-   <span data-ttu-id="82ea0-127">Itera através de nós, selecionando adequadamente os nós para o conjunto de resultados com base na avaliação da expressão.</span><span class="sxs-lookup"><span data-stu-id="82ea0-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="82ea0-128">Este é significativamente mais do que o trabalho feito pela consulta correspondente LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="82ea0-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="82ea0-129">A diferença de desempenho específico variam para diferentes tipos de consultas, mas em geral menos trabalho consultas LINQ to XML e, portanto, têm desempenho melhor, que avaliar expressões XPath usando <xref:System.Xml.XmlDocument>.</xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="82ea0-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ea0-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82ea0-130">See Also</span></span>  
 [<span data-ttu-id="82ea0-131">Desempenho (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82ea0-131">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)

