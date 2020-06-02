---
title: Atualizações dinâmicas a NodeLists e a NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 0199f24e9ef8dd28f91976edd50f78399dc893ef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292079"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="6ddd3-102">Atualizações dinâmicas a NodeLists e a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="6ddd3-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="6ddd3-103">Como **XmlNodeList** e **XmlNamedNodeMap** contêm um conjunto de nós, mas o documento XML é carregado na memória e está sendo alterado, o W3C (World Wide Web Consortium) indica que os objetos que contêm conjuntos de nós precisam ser dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="6ddd3-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="6ddd3-104">Isto é, se o documento subjacente é modificada, então os dados nesses dois objetos também deve alterar.</span><span class="sxs-lookup"><span data-stu-id="6ddd3-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="6ddd3-105">Portanto, se você tiver um **XmlNodeList** que contenha todos os elementos filho de um elemento específico (por exemplo, o elemento X), inclua um elemento adicional, o elemento Q, no documento sob o elemento X. **XmlNodeList** também deve ter esse novo elemento Q adicionado à coleção.</span><span class="sxs-lookup"><span data-stu-id="6ddd3-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="6ddd3-106">O mesmo vale em ordem inversa.</span><span class="sxs-lookup"><span data-stu-id="6ddd3-106">The same is true in reverse.</span></span> <span data-ttu-id="6ddd3-107">Se um nó é adicionado a **XmlNodeList**, o documento subjacente é atualizado também.</span><span class="sxs-lookup"><span data-stu-id="6ddd3-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ddd3-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="6ddd3-108">See also</span></span>

- [<span data-ttu-id="6ddd3-109">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="6ddd3-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
