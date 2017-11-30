---
title: Diretivas de folha de estilos inseridas em um documento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c5cfcc9f35e4a07e9426a4dd24c1e2f04985f16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="b746e-102">Diretivas de folha de estilos inseridas em um documento</span><span class="sxs-lookup"><span data-stu-id="b746e-102">Style Sheet Directives Embedded in a Document</span></span>
<span data-ttu-id="b746e-103">Ocasionalmente, existir XML contém a política de folha de estilos de `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="b746e-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="b746e-104">O Microsoft Internet Explorer aceita isso como uma alternativa para o `<?xml-stylesheet?>` sintaxe.</span><span class="sxs-lookup"><span data-stu-id="b746e-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="b746e-105">Quando os dados XML contém uma diretiva de `<?xml:stylesheet?>` , conforme mostrado nos seguintes dados, tentando carregar esses dados no modelo de objeto de documento XML (DOM) palavras-chave acionar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b746e-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 <span data-ttu-id="b746e-106">Isso ocorre porque o `<?xml:stylesheet?>` é considerado inválido **instrução de processamento** ao DOM.</span><span class="sxs-lookup"><span data-stu-id="b746e-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="b746e-107">Qualquer **instrução de processamento**, de acordo com os Namespaces na especificação XML, só podem ser nomes de dois-pontos não (NCNames), em vez de qualificado de nomes (QNames).</span><span class="sxs-lookup"><span data-stu-id="b746e-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>  
  
 <span data-ttu-id="b746e-108">Na seção 6 de Namespaces na especificação do XML, o efeito de ter o **carga** e **LoadXml** métodos estão em conformidade com a especificação é que, em um documento:</span><span class="sxs-lookup"><span data-stu-id="b746e-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>  
  
-   <span data-ttu-id="b746e-109">Todos os tipos de elemento e nomes de atributo contêm zero ou mais pontos.</span><span class="sxs-lookup"><span data-stu-id="b746e-109">All element types and attribute names contain either zero or one colon.</span></span>  
  
-   <span data-ttu-id="b746e-110">Nenhum nome de entidade, destino de ProcessingInstruction, ou nome de notação contém todos os dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="b746e-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>  
  
 <span data-ttu-id="b746e-111">Com `<?xml:stylesheet?>` que contém dois-pontos, você agora viola a regra no segundo marcador.</span><span class="sxs-lookup"><span data-stu-id="b746e-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>  
  
 <span data-ttu-id="b746e-112">De acordo com o World Wide Web Consortium (W3C) que associa folhas de estilo com a recomendação de versão 1,0 de documentos XML, localizado em www.w3.org/TR/xml-stylesheet, a instrução de processamento para associar uma folha de estilos XSLT com um documento XML é `<?xml-stylesheet?>`, com um sublinhado que substitui o separador dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="b746e-112">According to the World Wide Web Consortium (W3C) Associating Style Sheets with XML documents Version 1.0 Recommendation, located at www.w3.org/TR/xml-stylesheet, the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b746e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b746e-113">See Also</span></span>  
 [<span data-ttu-id="b746e-114">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="b746e-114">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
