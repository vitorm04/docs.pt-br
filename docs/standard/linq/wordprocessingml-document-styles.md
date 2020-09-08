---
title: Documento do WordprocessingML com estilos-LINQ to XML
description: Saiba mais sobre os documentos do WordprocessingML cujos parágrafos são formatados com estilos.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: 7864ce5163d9dfb316c8288850210becdf55dc2d
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551953"
---
# <a name="wordprocessingml-document-with-styles-linq-to-xml"></a><span data-ttu-id="ac85c-103">Documento do WordprocessingML com estilos (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ac85c-103">WordprocessingML document with styles (LINQ to XML)</span></span>

<span data-ttu-id="ac85c-104">Este artigo apresenta um documento do WordprocessingML que é mais complicado do que aquele na [forma XML de documentos do WordprocessingML](xml-shape-wordprocessingml-documents.md); especificamente, ele apresenta um documento cujos parágrafos são formatados com estilos.</span><span class="sxs-lookup"><span data-stu-id="ac85c-104">This article presents a WordprocessingML document that is more complicated than the one in [The XML shape of WordprocessingML documents](xml-shape-wordprocessingml-documents.md); specifically, it presents a document whose paragraphs are formatted with styles.</span></span>

<span data-ttu-id="ac85c-105">Para entender os estilos, é útil saber algo sobre a estrutura do documento.</span><span class="sxs-lookup"><span data-stu-id="ac85c-105">To understand styles, it's helpful to know something about document structure.</span></span> <span data-ttu-id="ac85c-106">Um documento do WordprocessingML é armazenado em um *pacote* que compõe as *partes*.</span><span class="sxs-lookup"><span data-stu-id="ac85c-106">A WordprocessingML document is stored in a *package* that comprises *parts*.</span></span> <span data-ttu-id="ac85c-107">Especificamente, o termo *pacote* corresponde a um arquivo zip e a *parte* do termo corresponde a um file armazenado no zip.</span><span class="sxs-lookup"><span data-stu-id="ac85c-107">Specifically, the term *package* corresponds to a ZIP archive and the term *part* corresponds to a file stored within the ZIP.</span></span> <span data-ttu-id="ac85c-108">Se um documento contiver parágrafos formatados com estilos, haverá uma parte do documento que contém os parágrafos que têm estilos aplicados a eles e uma parte de estilo que define os estilos referenciados na parte do documento.</span><span class="sxs-lookup"><span data-stu-id="ac85c-108">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them, and a style part that defines the styles referenced in the document part.</span></span>

<span data-ttu-id="ac85c-109">A maneira mais fácil de ver o XML que compõe um documento XML aberto do Office é executar o exemplo no [exemplo que gera as partes do documento XML aberto do Office](example-outputs-office-open-xml-document-parts.md).</span><span class="sxs-lookup"><span data-stu-id="ac85c-109">The easiest way to see the XML that makes up an Office Open XML document is to run the example in [Example that outputs Office Open XML document parts](example-outputs-office-open-xml-document-parts.md).</span></span>

<span data-ttu-id="ac85c-110">Ao acessar um pacote, você deve fazer isso por meio das relações entre as partes, não por meio de um caminho arbitrário.</span><span class="sxs-lookup"><span data-stu-id="ac85c-110">When you access a package, you should do so through the relationships among parts, not through an arbitrary path.</span></span> <span data-ttu-id="ac85c-111">Esse problema está além do escopo do tutorial atual, mas os programas de exemplo neste e em outros artigos do tutorial demonstram a abordagem correta.</span><span class="sxs-lookup"><span data-stu-id="ac85c-111">This issue is beyond the scope of the current tutorial, but the example programs in this and other tutorial articles demonstrate the correct approach.</span></span>

## <a name="example-a-document-that-uses-styles"></a><span data-ttu-id="ac85c-112">Exemplo: um documento que usa estilos</span><span class="sxs-lookup"><span data-stu-id="ac85c-112">Example: A document that uses styles</span></span>

<span data-ttu-id="ac85c-113">O documento a seguir tem parágrafos formatados com estilos.</span><span class="sxs-lookup"><span data-stu-id="ac85c-113">The following document has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="ac85c-114">O primeiro parágrafo tem o estilo `Heading1` e outros parágrafos têm o estilo `Code` ou o estilo padrão.</span><span class="sxs-lookup"><span data-stu-id="ac85c-114">The first paragraph has the style `Heading1` and other paragraphs have the `Code` style or the default style.</span></span> <span data-ttu-id="ac85c-115">Para parágrafos com estilos não padrão, os elementos de parágrafo têm um elemento filho chamado `w:pPr` , que, por sua vez, tem um elemento filho `w:pStyle` .</span><span class="sxs-lookup"><span data-stu-id="ac85c-115">For paragraphs with non-default styles the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="ac85c-116">Esse elemento tem um atributo, `w:val`, que contém o nome do estilo.</span><span class="sxs-lookup"><span data-stu-id="ac85c-116">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="ac85c-117">Para parágrafos com o estilo padrão, o elemento Paragraph não tem um `w:p.Pr` elemento filho.</span><span class="sxs-lookup"><span data-stu-id="ac85c-117">For paragraphs with the default style, the paragraph element doesn't have a `w:p.Pr` child element.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<w:document
    xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:o="urn:schemas-microsoft-com:office:office"
    xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"
    xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"
    xmlns:v="urn:schemas-microsoft-com:vml"
    xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"
    xmlns:w10="urn:schemas-microsoft-com:office:word"
    xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"
    xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">
  <w:body>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Heading1" />
      </w:pPr>
      <w:r>
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">
      <w:r>
        <w:t>The following example prints to the console.</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r>
        <w:t>using System;</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t>class Program {</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">    public static void </w:t>
      </w:r>
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">
        <w:r w:rsidRPr="00876F34">
          <w:t>Main</w:t>
        </w:r>
      </w:smartTag>
      <w:r w:rsidRPr="00876F34">
        <w:t>(string[] args) {</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">    }</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t>}</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">
      <w:r>
        <w:t>This example produces the following output:</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r>
        <w:t>Hello World</w:t>
      </w:r>
    </w:p>
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">
      <w:pgSz w:w="12240" w:h="15840" />
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />
      <w:cols w:space="720" />
      <w:docGrid w:linePitch="360" />
    </w:sectPr>
  </w:body>
</w:document>
```
