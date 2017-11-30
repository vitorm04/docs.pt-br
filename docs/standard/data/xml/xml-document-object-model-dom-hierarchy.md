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
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6dec61860fba5815b1dae802d280e8df6628ab91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="4ef96-102">Hierarquia DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="4ef96-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="4ef96-103">A ilustração a seguir mostra a hierarquia de classes para o DOM (Document Object Model) XML, com o nome do World Wide Web Consortium (W3C) entre parênteses junto com o nome da classe onde é relevante.</span><span class="sxs-lookup"><span data-stu-id="4ef96-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="4ef96-104">![Modelo de objeto de documento XML &#40; DOM &#41; hierarquia](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="4ef96-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="4ef96-105">Hierarquia DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="4ef96-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="4ef96-106">As seguintes classes não herdam a **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="4ef96-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="4ef96-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="4ef96-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="4ef96-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="4ef96-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="4ef96-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="4ef96-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="4ef96-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="4ef96-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="4ef96-111">O **XmlImplementation** classe é usada para criar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="4ef96-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="4ef96-112">Para obter mais informações, consulte [criação de documentos XML](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="4ef96-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="4ef96-113">O **XmlNamedNodeMap** classe manipula um conjunto ordenado de nós.</span><span class="sxs-lookup"><span data-stu-id="4ef96-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="4ef96-114">Para obter mais informações, consulte [recuperação não ordenada do nó por nome ou índice](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="4ef96-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="4ef96-115">O **XmlNodeList** classe manipula uma lista ordenada de nós.</span><span class="sxs-lookup"><span data-stu-id="4ef96-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="4ef96-116">Para obter mais informações, consulte [recuperação de nó ordenada pelo índice](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="4ef96-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="4ef96-117">O **XmlNodeChangedEventArgs** classe manipula os manipuladores de eventos registrados no **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="4ef96-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="4ef96-118">Para obter mais informações, consulte [manipulação de eventos em um documento XML usando o XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="4ef96-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="4ef96-119">O **XmlLinkedNode** classe herda de **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="4ef96-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="4ef96-120">Seu objetivo é substituir dois métodos de **XmlNode**: o **PreviousSibling** e **NextSibling** métodos.</span><span class="sxs-lookup"><span data-stu-id="4ef96-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="4ef96-121">Esses métodos substituídos são então herdados e usados por **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, e **XmlProcessingInstruction**, que são classes que possuem irmão anterior e próximo.</span><span class="sxs-lookup"><span data-stu-id="4ef96-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef96-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ef96-122">See Also</span></span>  
 [<span data-ttu-id="4ef96-123">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="4ef96-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
