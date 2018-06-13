---
title: Atualizações dinâmicas a NodeLists e a NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1de133d0208f1b86ad3240cdc00d8016af0a160c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568960"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="c91e8-102">Atualizações dinâmicas a NodeLists e a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="c91e8-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="c91e8-103">Como **XmlNodeList** e **XmlNamedNodeMap** contêm um conjunto de nós, mas o documento XML é carregado na memória e está sendo alterado, o W3C (World Wide Web Consortium) indica que os objetos que contêm conjuntos de nós precisam ser dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="c91e8-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="c91e8-104">Isto é, se o documento subjacente é modificada, então os dados nesses dois objetos também deve alterar.</span><span class="sxs-lookup"><span data-stu-id="c91e8-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="c91e8-105">Portanto, se você tiver um **XmlNodeList** que contenha todos os elementos filho de um elemento específico (por exemplo, o elemento X), inclua um elemento adicional, o elemento Q, no documento sob o elemento X. **XmlNodeList** também deve ter esse novo elemento Q adicionado à coleção.</span><span class="sxs-lookup"><span data-stu-id="c91e8-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="c91e8-106">O mesmo vale em ordem inversa.</span><span class="sxs-lookup"><span data-stu-id="c91e8-106">The same is true in reverse.</span></span> <span data-ttu-id="c91e8-107">Se um nó é adicionado a **XmlNodeList**, o documento subjacente é atualizado também.</span><span class="sxs-lookup"><span data-stu-id="c91e8-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c91e8-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c91e8-108">See Also</span></span>  
 [<span data-ttu-id="c91e8-109">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="c91e8-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
