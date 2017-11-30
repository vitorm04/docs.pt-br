---
title: "Tipos de nós reconhecidos com consultas XPath"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c1e48bbfd6388686fdb83f08668f7f0234275a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="fe987-102">Tipos de nós reconhecidos com consultas XPath</span><span class="sxs-lookup"><span data-stu-id="fe987-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="fe987-103">Os tipos de nós reconhecidas em uma consulta XPath não são os mesmos tipos de nós localizados em Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="fe987-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="fe987-104">Tipos de nós XPath W3C</span><span class="sxs-lookup"><span data-stu-id="fe987-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="fe987-105">Os tipos de nós reconhecidas em uma consulta XPath não são tipos de nós localizados em Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="fe987-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="fe987-106">A seguir estão os tipos de nós XPath representados pela enumeração de <xref:System.Xml.XPath.XPathNodeType> .</span><span class="sxs-lookup"><span data-stu-id="fe987-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNodeType.All>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Element>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Root>  
  
-   <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Text>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 <span data-ttu-id="fe987-107">Esses tipos de nós são baseados no modelo de dados XPath, onde os nós são derivados do conjunto de informações XML.</span><span class="sxs-lookup"><span data-stu-id="fe987-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="fe987-108">Os tipos de nós de <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> e de <xref:System.Xml.XPath.XPathNodeType.Whitespace> são extensões do Microsoft .NET Framework para tipos de nós de base descritos no modelo de dados XPath.</span><span class="sxs-lookup"><span data-stu-id="fe987-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="fe987-109">O tipo de nó de atributo é usado de forma diferente no modelo de dados XPath do que está em DOM.</span><span class="sxs-lookup"><span data-stu-id="fe987-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="fe987-110">No modelo de dados XPath, o nó do elemento tem um conjunto de nós de atributo relacionados a ele e o nó do elemento é o pai de cada nó de atributo.</span><span class="sxs-lookup"><span data-stu-id="fe987-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="fe987-111">No entanto, em DOM, o nó do elemento é o proprietário e não o pai.</span><span class="sxs-lookup"><span data-stu-id="fe987-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="fe987-112">Em ambos os modelos, o atributo e os nós de namespace não são considerados nós filho do nó do elemento.</span><span class="sxs-lookup"><span data-stu-id="fe987-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="fe987-113">O tipo de nó de namespace é uma adição ao modelo de dados XPath e não é um tipo de nó reconhecido DOM.</span><span class="sxs-lookup"><span data-stu-id="fe987-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="fe987-114">Para obter mais informações sobre como navegar de elemento, atributo e nós de namespace, consulte o [nó definido navegação usando XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) e [atributo e Namespace nó de navegação usando XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) tópicos.</span><span class="sxs-lookup"><span data-stu-id="fe987-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe987-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe987-115">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="fe987-116">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="fe987-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="fe987-117">Selecionar dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="fe987-117">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="fe987-118">Avalia as expressões XPath usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="fe987-118">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="fe987-119">Nós compatíveis usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="fe987-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="fe987-120">Consultas XPath e namespaces</span><span class="sxs-lookup"><span data-stu-id="fe987-120">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="fe987-121">Expressões XPath compilados</span><span class="sxs-lookup"><span data-stu-id="fe987-121">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
