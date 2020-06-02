---
title: Removendo os nós DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: 5df95700bb1e84aa5f3adcc752b2314dc964477b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288635"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="5a9b0-102">Removendo os nós DOM</span><span class="sxs-lookup"><span data-stu-id="5a9b0-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="5a9b0-103">Para remover um nó de (DOM) modelo de objeto de documento, use o método de <xref:System.Xml.XmlNode.RemoveChild%2A> para remover um nó específico.</span><span class="sxs-lookup"><span data-stu-id="5a9b0-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="5a9b0-104">Quando você remove um nó, o método remove a subárvore que pertence ao nó que está sendo removido; isto é, se não é um nó folha.</span><span class="sxs-lookup"><span data-stu-id="5a9b0-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="5a9b0-105">Para remover os vários nós DOM, use o método de <xref:System.Xml.XmlNode.RemoveAll%2A> para remover todos os filhos e atributos, se aplicável, do nó atual.</span><span class="sxs-lookup"><span data-stu-id="5a9b0-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="5a9b0-106">Se você estiver trabalhando com <xref:System.Xml.XmlNamedNodeMap>, você pode remover um nó usando o método <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> .</span><span class="sxs-lookup"><span data-stu-id="5a9b0-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="5a9b0-107">Para remover os atributos, confira [Removendo os atributos de um nó no elemento DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="5a9b0-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a9b0-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="5a9b0-108">See also</span></span>

- [<span data-ttu-id="5a9b0-109">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="5a9b0-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
