---
title: "Avalia as expressões XPath usando XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d4515b8ebea338a153319dfd02eab8d389b843b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="2bc4f-102">Avalia as expressões XPath usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2bc4f-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="2bc4f-103">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece o método de <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> para avaliar uma expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="2bc4f-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="2bc4f-104">O método de <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> usa uma expressão XPath, avalia-a e retorna um tipo XPath W3C de booleano, de número, de cadeia de caracteres, ou de conjunto do nó com base no resultado da expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="2bc4f-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="2bc4f-105">O método de avaliação</span><span class="sxs-lookup"><span data-stu-id="2bc4f-105">The Evaluate Method</span></span>  
 <span data-ttu-id="2bc4f-106">O método de <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> usa uma expressão XPath, avalia-a, e retorna um resultado de tipo booleano (<xref:System.Boolean>), o número (<xref:System.Double>), a cadeia de caracteres (<xref:System.String>), ou do conjunto de nó (<xref:System.Xml.XPath.XPathNodeIterator>).</span><span class="sxs-lookup"><span data-stu-id="2bc4f-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="2bc4f-107">Por exemplo, o método de <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> pode ser usado em um método matemático.</span><span class="sxs-lookup"><span data-stu-id="2bc4f-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="2bc4f-108">O código exemplo a seguir calcula o custo total de todos os livros no arquivo de `books.xml` .</span><span class="sxs-lookup"><span data-stu-id="2bc4f-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="2bc4f-109">O exemplo usa o arquivo `books.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="2bc4f-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="2bc4f-110">funções de posição e o último</span><span class="sxs-lookup"><span data-stu-id="2bc4f-110">position and last Functions</span></span>  
 <span data-ttu-id="2bc4f-111">O método de <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> está sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="2bc4f-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="2bc4f-112">Um dos métodos de <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> utiliza um objeto de <xref:System.Xml.XPath.XPathNodeIterator> como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2bc4f-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="2bc4f-113">Este método de <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> de detalhe é idêntico ao método de <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> que utiliza apenas um objeto de <xref:System.Xml.XPath.XPathExpression> como um parâmetro, exceto que permite que a um nó do argumento especifica o contexto atual para executar sobre a avaliação.</span><span class="sxs-lookup"><span data-stu-id="2bc4f-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="2bc4f-114">Este contexto é necessário para o XPath `position()` e funções de `last()` que são relativos ao nó atual de contexto.</span><span class="sxs-lookup"><span data-stu-id="2bc4f-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="2bc4f-115">A menos que usado como um predicado em uma etapa local, `position()` e funções de `last()` requerem uma referência a um nó definida para ser avaliado de outra forma, `position` e funções `last`de retorno de `0` .</span><span class="sxs-lookup"><span data-stu-id="2bc4f-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc4f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bc4f-116">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="2bc4f-117">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="2bc4f-117">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="2bc4f-118">Selecionar dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2bc4f-118">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="2bc4f-119">Correspondência de nós usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2bc4f-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="2bc4f-120">Tipos de nós reconhecidos com consultas XPath</span><span class="sxs-lookup"><span data-stu-id="2bc4f-120">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="2bc4f-121">Consultas e Namespaces de XPath</span><span class="sxs-lookup"><span data-stu-id="2bc4f-121">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="2bc4f-122">Expressões XPath compilados</span><span class="sxs-lookup"><span data-stu-id="2bc4f-122">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
