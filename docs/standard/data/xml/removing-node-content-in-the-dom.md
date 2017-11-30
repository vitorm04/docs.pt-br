---
title: "Removendo conteúdo do nó em DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76be90829a414b091d3b311b96bf9bab9a2b56ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="0cc09-102">Removendo conteúdo do nó em DOM</span><span class="sxs-lookup"><span data-stu-id="0cc09-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="0cc09-103">Para os tipos de nós que herdam de <xref:System.Xml.XmlCharacterData>, que são <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, e os tipos de nós de <xref:System.Xml.XmlSignificantWhitespace> , você pode remover os caracteres usando o método de <xref:System.Xml.XmlCharacterData.DeleteData%2A> , que remove um intervalo de caracteres de nó.</span><span class="sxs-lookup"><span data-stu-id="0cc09-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="0cc09-104">Se você deseja remover completamente o conteúdo, você remover o nó que contém o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="0cc09-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="0cc09-105">Se você desejar manter o nó, mas o conteúdo está incorreto, então modificar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="0cc09-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="0cc09-106">Para obter informações sobre como modificar o conteúdo de um nó, consulte [modificando nós, conteúdo e os valores em um documento XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="0cc09-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc09-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cc09-107">See Also</span></span>  
 [<span data-ttu-id="0cc09-108">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="0cc09-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
