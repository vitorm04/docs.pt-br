---
title: Espaço em branco e tratamento processamento de espaço em branco para carregar os DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8e2279023029b5047cc7d9b4d0d97ac1f21e3f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569064"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="53b42-102">Espaço em branco e tratamento processamento de espaço em branco para carregar os DOM</span><span class="sxs-lookup"><span data-stu-id="53b42-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="53b42-103">Ao carregar o documento, você pode definir a opção de preservar espaço em branco e criar nós de **XmlWhitespace** na árvore do documento.</span><span class="sxs-lookup"><span data-stu-id="53b42-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="53b42-104">Para criar nós de espaço em branco, defina a propriedade **PreserveWhitespace** como verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="53b42-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="53b42-105">Se a propriedade for definida como **falso**, que é o padrão, os nós de espaço em branco não serão criados.</span><span class="sxs-lookup"><span data-stu-id="53b42-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="53b42-106">Os nós significativos de espaços em branco são preservados sempre, e os nós **XmlSignificantWhitespace** sempre são criados na memória para representar esses dados, independentemente da configuração de sinalizador de **PreserveWhitespace**.</span><span class="sxs-lookup"><span data-stu-id="53b42-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="53b42-107">Se o documento for carregado de um leitor, a configuração da propriedade do sinalizador **PreserveWhitespace** na classe **XmlDocument** afetará a criação de nós **XmlWhitespace** somente quando a propriedade **WhitespaceHandling** em **XmlTextReader** não for definida como **WhitespaceHandling.None**.</span><span class="sxs-lookup"><span data-stu-id="53b42-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="53b42-108">É o valor da propriedade **WhitespaceHandling** o leitor que tem precedência sobre a configuração de aquele sinalizador no **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="53b42-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="53b42-109">Para saber mais sobre **XmlSignificantWhitespace**, veja <xref:System.Xml.XmlSignificantWhitespace>.</span><span class="sxs-lookup"><span data-stu-id="53b42-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b42-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53b42-110">See Also</span></span>  
 [<span data-ttu-id="53b42-111">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="53b42-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
