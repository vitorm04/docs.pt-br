---
title: "Espaço em branco e tratamento processamento de espaço em branco para carregar os DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82401a18132801f9aa5368832b96be3cb67a8642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="e2153-102">Espaço em branco e tratamento processamento de espaço em branco para carregar os DOM</span><span class="sxs-lookup"><span data-stu-id="e2153-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="e2153-103">Ao carregar o documento, você pode definir a opção para preservar espaço em branco e criar **XmlWhitespace** nós na árvore do documento.</span><span class="sxs-lookup"><span data-stu-id="e2153-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="e2153-104">Para criar nós de espaços em branco, defina o **PreserveWhitespace** propriedade como true.</span><span class="sxs-lookup"><span data-stu-id="e2153-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="e2153-105">Se a propriedade é definida como **false**, que é o padrão, nós de espaço em branco não são criados.</span><span class="sxs-lookup"><span data-stu-id="e2153-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="e2153-106">Nós de espaços em branco são sempre preservados, e **XmlSignificantWhitespace** nós sempre são criados na memória para representar esses dados, independentemente da configuração do **PreserveWhitespace** sinalizador.</span><span class="sxs-lookup"><span data-stu-id="e2153-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="e2153-107">Se o documento é carregado de um leitor, em seguida, a configuração do **PreserveWhitespace** sinalizador de propriedade no **XmlDocument** classe afeta a criação de **XmlWhitespace** nós somente quando o **WhitespaceHandling** propriedade o **XmlTextReader** não está definido como **eram**.</span><span class="sxs-lookup"><span data-stu-id="e2153-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="e2153-108">É o valor de **WhitespaceHandling** propriedade do leitor que tem precedência sobre a configuração do sinalizador no **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="e2153-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="e2153-109">Para obter mais informações sobre **XmlSignificantWhitespace**, consulte <xref:System.Xml.XmlSignificantWhitespace>.</span><span class="sxs-lookup"><span data-stu-id="e2153-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2153-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2153-110">See Also</span></span>  
 [<span data-ttu-id="e2153-111">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="e2153-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
