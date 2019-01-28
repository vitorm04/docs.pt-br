---
title: Navegação do nó usando XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58adf0251fdc7427f493e8bf9947c081bfccd2a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618088"
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="d4b8c-102">Navegação do nó usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d4b8c-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="d4b8c-103">Você pode navegar sobre nós em <xref:System.Xml.XPath.XPathDocument> ou o objeto de <xref:System.Xml.XmlDocument> que usa os métodos definidos de navegação do nó de <xref:System.Xml.XPath.XPathNavigator> classe.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="d4b8c-104">Você pode navegar sobre todos os nós ou sobre um conjunto selecionado de nós retornados por um dos métodos de seleção de classe de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="d4b8c-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="d4b8c-105">Navegação do nó de elemento</span><span class="sxs-lookup"><span data-stu-id="d4b8c-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="d4b8c-106">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece vários métodos usados para navegar em nós do elemento.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="d4b8c-107">A tabela a seguir mostra os métodos de navegação disponíveis e uma descrição de como se movem; isso não inclui os métodos usados para navegar nós de atributo e de namespace.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="d4b8c-108">Para saber mais sobre como escolher nós no objeto <xref:System.Xml.XPath.XPathNavigator>, confira [Selecionar, avaliar e corresponder dados XML usando XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="d4b8c-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="d4b8c-109">Para saber mais sobre a navegação de nós de atributo e do namespace, confira [Navegação do nó de atributo e do namespace usando XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="d4b8c-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="d4b8c-110">Método</span><span class="sxs-lookup"><span data-stu-id="d4b8c-110">Method</span></span>|<span data-ttu-id="d4b8c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d4b8c-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="d4b8c-112">Move <xref:System.Xml.XPath.XPathNavigator> a mesma posição de <xref:System.Xml.XPath.XPathNavigator> especificou.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="d4b8c-113">Move <xref:System.Xml.XPath.XPathNavigator> a um nó filho do nó atual.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="d4b8c-114">Move <xref:System.Xml.XPath.XPathNavigator> ao primeiro nó irmãos do nó atual.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="d4b8c-115">Move <xref:System.Xml.XPath.XPathNavigator> ao primeiro nó filho do nó atual.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="d4b8c-116">Move <xref:System.Xml.XPath.XPathNavigator> ao elemento especificado na ordem de documento.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="d4b8c-117">Move <xref:System.Xml.XPath.XPathNavigator> o nó que possui um atributo do tipo `ID` com um valor que corresponde <xref:System.String>determinado.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="d4b8c-118">Move <xref:System.Xml.XPath.XPathNavigator> o nó seguir irmãos do nó atual.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="d4b8c-119">Move <xref:System.Xml.XPath.XPathNavigator> o nó pai do nó atual.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="d4b8c-120">Move <xref:System.Xml.XPath.XPathNavigator> o nó anterior irmãos do nó atual.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="d4b8c-121">Move <xref:System.Xml.XPath.XPathNavigator> ao nó raiz de documento XML.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="d4b8c-122">Comentários e navegação do nó de instrução de processamento</span><span class="sxs-lookup"><span data-stu-id="d4b8c-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="d4b8c-123">Os seguintes métodos da classe <xref:System.Xml.XPath.XPathNavigator> são válidos para mover para comentários ou as instruções de processamento de outros nós em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="d4b8c-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="d4b8c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4b8c-124">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="d4b8c-125">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="d4b8c-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="d4b8c-126">Navegação do nó de atributo e de namespace usando o XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d4b8c-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="d4b8c-127">Extrair dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d4b8c-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="d4b8c-128">Acessando dados XML fortemente tipados usando o XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d4b8c-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
