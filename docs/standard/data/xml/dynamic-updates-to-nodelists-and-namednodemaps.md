---
title: "Atualizações dinâmicas a NodeLists e a NamedNodeMaps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 459d746ff278ac4affa0318c1fad0aeb6a73e560
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="ccf85-102">Atualizações dinâmicas a NodeLists e a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="ccf85-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="ccf85-103">Porque o **XmlNodeList** e **XmlNamedNodeMap** contêm um conjunto de nós, mas o documento XML é carregado na memória e está sendo modificado, o World Wide Web Consortium (W3C) indica que esses objetos que contêm conjuntos de nós precisam ser dinâmica.</span><span class="sxs-lookup"><span data-stu-id="ccf85-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="ccf85-104">Isto é, se o documento subjacente é modificada, então os dados nesses dois objetos também deve alterar.</span><span class="sxs-lookup"><span data-stu-id="ccf85-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="ccf85-105">Portanto, se você tiver um **XmlNodeList** que contém todos os elementos filho de um elemento específico (por exemplo, o elemento X), em seguida, adicione um elemento adicional, o elemento P, o documento em elemento X. O **XmlNodeList** devem ter esse novo elemento p adicionado à sua coleção.</span><span class="sxs-lookup"><span data-stu-id="ccf85-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="ccf85-106">O mesmo vale em ordem inversa.</span><span class="sxs-lookup"><span data-stu-id="ccf85-106">The same is true in reverse.</span></span> <span data-ttu-id="ccf85-107">Se um nó é adicionado a **XmlNodeList**, o documento subjacente também é atualizado.</span><span class="sxs-lookup"><span data-stu-id="ccf85-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf85-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccf85-108">See Also</span></span>  
 [<span data-ttu-id="ccf85-109">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="ccf85-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
