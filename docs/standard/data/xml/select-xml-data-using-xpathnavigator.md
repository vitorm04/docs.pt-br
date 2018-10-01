---
title: Selecionar dados XML usando XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fea54d36759b12b01fa7a68748d069c7890d84e4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070507"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="c8d11-102">Selecionar dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c8d11-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="c8d11-103">A classe <xref:System.Xml.XPath.XPathNavigator> fornece um conjunto de métodos usados para selecionar um conjunto de nós em um objeto <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> usando uma expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="c8d11-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="c8d11-104">Depois de selecionado, você pode iterar sobre o conjunto de nós selecionado.</span><span class="sxs-lookup"><span data-stu-id="c8d11-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="c8d11-105">Métodos de seleção XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c8d11-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="c8d11-106">A classe <xref:System.Xml.XPath.XPathNavigator> fornece um conjunto de métodos usados para selecionar um conjunto de nós em um objeto <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> usando uma expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="c8d11-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="c8d11-107">A classe <xref:System.Xml.XPath.XPathNavigator> também fornece um conjunto de métodos otimizados para selecionar nós ancestrais, filhos ou descendentes mais rapidamente do que usar uma expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="c8d11-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="c8d11-108">O conjunto de nós selecionado é retornado em um objeto <xref:System.Xml.XPath.XPathNodeIterator> ou em um objeto <xref:System.Xml.XPath.XPathNavigator> no caso de um único nó selecionado.</span><span class="sxs-lookup"><span data-stu-id="c8d11-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="c8d11-109">Selecionando nós usando expressões XPath</span><span class="sxs-lookup"><span data-stu-id="c8d11-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="c8d11-110">Para selecionar um conjunto de nós usando uma expressão XPath, use um dos seguintes métodos de seleção.</span><span class="sxs-lookup"><span data-stu-id="c8d11-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="c8d11-111">Quando chamados, esses métodos retornam um conjunto de nós que você pode navegar livremente usando um objeto <xref:System.Xml.XPath.XPathNodeIterator> ou um objeto <xref:System.Xml.XPath.XPathNavigator> no caso de um único nó selecionado.</span><span class="sxs-lookup"><span data-stu-id="c8d11-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="c8d11-112">A navegação com um objeto <xref:System.Xml.XPath.XPathNodeIterator> não afeta a posição do objeto <xref:System.Xml.XPath.XPathNavigator> usado para criá-lo.</span><span class="sxs-lookup"><span data-stu-id="c8d11-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="c8d11-113">O objeto <xref:System.Xml.XPath.XPathNavigator> retornado dos métodos <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> é posicionado no único nó retornado e também não afeta a posição do objeto <xref:System.Xml.XPath.XPathNavigator> usado para criá-lo.</span><span class="sxs-lookup"><span data-stu-id="c8d11-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="c8d11-114">O exemplo a seguir mostra a criação de um objeto <xref:System.Xml.XPath.XPathNavigator> de um objeto <xref:System.Xml.XPath.XPathDocument>, o uso do método <xref:System.Xml.XPath.XPathNavigator.Select%2A> para selecionar nós no objeto <xref:System.Xml.XPath.XPathDocument> e o uso do objeto <xref:System.Xml.XPath.XPathNodeIterator> para iterar sobre os nós selecionados.</span><span class="sxs-lookup"><span data-stu-id="c8d11-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 <span data-ttu-id="c8d11-115">O exemplo usa o arquivo `books.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="c8d11-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="c8d11-116">Métodos de seleção otimizados</span><span class="sxs-lookup"><span data-stu-id="c8d11-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="c8d11-117">Os métodos <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> e <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> da classe <xref:System.Xml.XPath.XPathNavigator> representam as expressões XPath comumente usadas para recuperar os nós filho, descendentes e ancestrais.</span><span class="sxs-lookup"><span data-stu-id="c8d11-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="c8d11-118">Esses métodos são otimizados para desempenho e são mais rápidos do que as expressões XPath correspondentes.</span><span class="sxs-lookup"><span data-stu-id="c8d11-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="c8d11-119">Os métodos <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> e <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> selecionam os nós ancestrais, filho e descendentes com base em um valor <xref:System.Xml.XPath.XPathNodeType> ou o nome local e o URI do namespace dos nós a serem selecionados.</span><span class="sxs-lookup"><span data-stu-id="c8d11-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="c8d11-120">Os nós ancestrais, filho e descendentes selecionados são retornados em um objeto <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="c8d11-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8d11-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8d11-121">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="c8d11-122">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="c8d11-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="c8d11-123">Avaliar as expressões XPath usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c8d11-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
- [<span data-ttu-id="c8d11-124">Correspondência de nós usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c8d11-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
- [<span data-ttu-id="c8d11-125">Tipos de nós reconhecidos com consultas XPath</span><span class="sxs-lookup"><span data-stu-id="c8d11-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [<span data-ttu-id="c8d11-126">Consultas e Namespaces de XPath</span><span class="sxs-lookup"><span data-stu-id="c8d11-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
- [<span data-ttu-id="c8d11-127">Expressões XPath compilados</span><span class="sxs-lookup"><span data-stu-id="c8d11-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
