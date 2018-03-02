---
title: Hierarquia DOM (Document Object Model) XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d2ffaa994ce3c9b02ed0937967845be1b803f6d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="0a967-102">Hierarquia DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="0a967-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="0a967-103">A ilustração a seguir mostra a hierarquia de classes para o DOM (Document Object Model) XML, com o nome do World Wide Web Consortium (W3C) entre parênteses junto com o nome da classe onde é relevante.</span><span class="sxs-lookup"><span data-stu-id="0a967-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="0a967-104">![Modelo de objeto de documento XML &#40;DOM&#41; hierarquia](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="0a967-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="0a967-105">Hierarquia DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="0a967-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="0a967-106">As seguintes classes não herdam de **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="0a967-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="0a967-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="0a967-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="0a967-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="0a967-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="0a967-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="0a967-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="0a967-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="0a967-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="0a967-111">A classe **XmlImplementation** é usada para criar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="0a967-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="0a967-112">Para saber mais, confira [Criação de documento XML](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="0a967-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="0a967-113">A classe **XmlNamedNodeMap** manipula um conjunto não ordenado de nós.</span><span class="sxs-lookup"><span data-stu-id="0a967-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="0a967-114">Para saber mais, confira [Recuperação não ordenada de nós por nome ou índice](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="0a967-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="0a967-115">A classe **XmlNodeList** manipula uma lista ordenada de nós.</span><span class="sxs-lookup"><span data-stu-id="0a967-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="0a967-116">Para saber mais, confira [Recuperação ordenada de nós por índice](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="0a967-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="0a967-117">A classe **XmlNodeChangedEventArgs** manipula os manipuladores de eventos registrados em **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a967-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="0a967-118">Para saber mais, confira [Manipulação de eventos em um documento XML usando XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="0a967-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="0a967-119">A classe **XmlLinkedNode** herda de **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="0a967-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="0a967-120">Sua finalidade é substituir dois métodos de **XmlNode**: os métodos **PreviousSibling** e **NextSibling**.</span><span class="sxs-lookup"><span data-stu-id="0a967-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="0a967-121">Esses métodos substituídos são então herdados e usados por **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference** e **XmlProcessingInstruction**, que são classes que têm irmãos anteriores e seguintes.</span><span class="sxs-lookup"><span data-stu-id="0a967-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a967-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a967-122">See Also</span></span>  
 [<span data-ttu-id="0a967-123">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="0a967-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
