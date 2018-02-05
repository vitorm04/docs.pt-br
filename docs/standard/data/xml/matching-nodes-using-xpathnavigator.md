---
title: "Nós compatíveis usando XPathNavigator"
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
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 06849e20386f0eecb55fdf906f78896828b9946e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="71346-102">Nós compatíveis usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="71346-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="71346-103">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece o método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> para determinar se um nó corresponde uma expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="71346-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="71346-104">O método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> usa uma expressão XPath como entrada e retorna <xref:System.Boolean> que indica se o nó atual corresponde a expressão XPath determinada ou o objeto compilado dado de <xref:System.Xml.XPath.XPathExpression> .</span><span class="sxs-lookup"><span data-stu-id="71346-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="71346-105">Nós compatíveis</span><span class="sxs-lookup"><span data-stu-id="71346-105">Matching Nodes</span></span>  
 <span data-ttu-id="71346-106">O método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retorna `true` se o nó atual corresponde a expressão XPath especificada.</span><span class="sxs-lookup"><span data-stu-id="71346-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="71346-107">Por exemplo, no exemplo de código que segue, o método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retornará `true` se o nó atual é o elemento `b`, e o elemento `b` tem um atributo `c`.</span><span class="sxs-lookup"><span data-stu-id="71346-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71346-108">O método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> não altera o estado de <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="71346-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a><span data-ttu-id="71346-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71346-109">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="71346-110">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="71346-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="71346-111">Selecionar dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="71346-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="71346-112">Avaliar as expressões XPath usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="71346-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="71346-113">Tipos de nós reconhecidos com consultas XPath</span><span class="sxs-lookup"><span data-stu-id="71346-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="71346-114">Consultas e Namespaces de XPath</span><span class="sxs-lookup"><span data-stu-id="71346-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="71346-115">Expressões XPath compilados</span><span class="sxs-lookup"><span data-stu-id="71346-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
