---
title: Diretivas de folha de estilos inseridas em um documento
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08bd33aab6cbeeeb9060f3de3565a05896c6ba7f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001341"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="6433b-102">Diretivas de folha de estilos inseridas em um documento</span><span class="sxs-lookup"><span data-stu-id="6433b-102">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="6433b-103">Ocasionalmente, existir XML contém a política de folha de estilos de `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="6433b-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="6433b-104">O Microsoft Internet Explorer aceita isso como uma alternativa à sintaxe `<?xml-stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="6433b-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="6433b-105">Quando os dados XML contém uma diretiva de `<?xml:stylesheet?>` , conforme mostrado nos seguintes dados, tentando carregar esses dados no modelo de objeto de documento XML (DOM) palavras-chave acionar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="6433b-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="6433b-106">Isso ocorre porque `<?xml:stylesheet?>` é considerado um **ProcessingInstruction** inválido para DOM.</span><span class="sxs-lookup"><span data-stu-id="6433b-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="6433b-107">Qualquer **ProcessingInstruction**, de acordo com os namespaces na especificação XML, só pode ser nomes de sem dois-pontos (NCNames), diferentemente de nomes qualificados (QNames).</span><span class="sxs-lookup"><span data-stu-id="6433b-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="6433b-108">Conforme a seção 6 de Namespaces na especificação XML, o efeito de fazer os métodos **Load** e **LoadXml** obedecerem à especificação é que, em um documento:</span><span class="sxs-lookup"><span data-stu-id="6433b-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="6433b-109">Todos os tipos de elemento e nomes de atributo contêm zero ou mais pontos.</span><span class="sxs-lookup"><span data-stu-id="6433b-109">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="6433b-110">Nenhum nome de entidade, destino de ProcessingInstruction, ou nome de notação contém todos os dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="6433b-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="6433b-111">Com `<?xml:stylesheet?>` que contém dois-pontos, você agora viola a regra no segundo marcador.</span><span class="sxs-lookup"><span data-stu-id="6433b-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="6433b-112">De acordo com a recomendação [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/) (Associando folhas de estilos a documentos XML versão 1.0) do W3C (World Wide Web Consortium), a instrução de processamento para associar uma folha de estilos XSLT a um documento XML é `<?xml-stylesheet?>`, com um traço substituindo dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="6433b-112">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="6433b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6433b-113">See Also</span></span>

[<span data-ttu-id="6433b-114">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="6433b-114">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)  