---
title: Removendo conteúdo do nó em DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 737766586ee920a87c25dd42896bdfb14ae69d98
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44205212"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="487cc-102">Removendo conteúdo do nó em DOM</span><span class="sxs-lookup"><span data-stu-id="487cc-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="487cc-103">Para os tipos de nós que herdam de <xref:System.Xml.XmlCharacterData>, que são <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, e os tipos de nós de <xref:System.Xml.XmlSignificantWhitespace> , você pode remover os caracteres usando o método de <xref:System.Xml.XmlCharacterData.DeleteData%2A> , que remove um intervalo de caracteres de nó.</span><span class="sxs-lookup"><span data-stu-id="487cc-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="487cc-104">Se você deseja remover completamente o conteúdo, você remover o nó que contém o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="487cc-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="487cc-105">Se você desejar manter o nó, mas o conteúdo está incorreto, então modificar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="487cc-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="487cc-106">Para saber mais sobre como alterar o conteúdo de um nó, confira [Modificando nós, conteúdo e valores em um documento XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="487cc-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="487cc-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="487cc-107">See also</span></span>

- [<span data-ttu-id="487cc-108">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="487cc-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
