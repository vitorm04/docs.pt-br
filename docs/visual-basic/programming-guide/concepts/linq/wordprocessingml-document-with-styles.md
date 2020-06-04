---
title: Documento do WordprocessingML com Styles2
ms.date: 07/20/2015
ms.assetid: a9136e4d-c368-4661-8049-7d45c679a236
ms.openlocfilehash: caf80014077bf57dc1ffb8eaeac6390cf4258015
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403544"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="7a54c-102">Documento de WordprocessingML com estilos</span><span class="sxs-lookup"><span data-stu-id="7a54c-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="7a54c-103">Um documentos mais complicados de WordprocessingML têm os parágrafos que são formatados com estilos.</span><span class="sxs-lookup"><span data-stu-id="7a54c-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="7a54c-104">Quaisquer notas sobre a composição de documentos de WordprocessingML são úteis.</span><span class="sxs-lookup"><span data-stu-id="7a54c-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="7a54c-105">Documentos de WordprocessingML são armazenados em pacotes.</span><span class="sxs-lookup"><span data-stu-id="7a54c-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="7a54c-106">Pacotes têm várias partes (partes tem um significado explícito quando usadas no contexto de pacotes; essencialmente, as partes são arquivos que são fechados juntos para entender um pacote).</span><span class="sxs-lookup"><span data-stu-id="7a54c-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="7a54c-107">Se um documento contém os parágrafos que são formatados com estilos, haverá uma parte do documento que contém os parágrafos que possuem os estilos aplicados a eles.</span><span class="sxs-lookup"><span data-stu-id="7a54c-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="7a54c-108">Também haverá uma parte de estilo que contém os estilos que são referenciados pelo documento.</span><span class="sxs-lookup"><span data-stu-id="7a54c-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="7a54c-109">Para acessar pacotes, é importante que você faz isso com relações entre as partes, em vez de usar um caminho arbitrário.</span><span class="sxs-lookup"><span data-stu-id="7a54c-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="7a54c-110">Esse problema está além do escopo do tutorial de Manipulando conteúdo em um documento WordprocessingML, mas os programas de exemplo que são incluídos neste tutorial demonstram a abordagem correta.</span><span class="sxs-lookup"><span data-stu-id="7a54c-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="7a54c-111">Um documento que use estilos</span><span class="sxs-lookup"><span data-stu-id="7a54c-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="7a54c-112">O exemplo de WordML apresentado na [forma de documentos WordprocessingML (Visual Basic)](shape-of-wordprocessingml-documents.md) é um bem simples.</span><span class="sxs-lookup"><span data-stu-id="7a54c-112">The WordML example presented in the [Shape of WordprocessingML Documents (Visual Basic)](shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="7a54c-113">O seguinte documento é mais complicado: Tem os parágrafos que são formatados com estilos.</span><span class="sxs-lookup"><span data-stu-id="7a54c-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="7a54c-114">A maneira mais fácil de ver o XML que compõe um documento XML aberto do Office é executar o [exemplo que gera as partes do documento XML aberto do Office (Visual Basic)](example-that-outputs-office-open-xml-document-parts.md).</span><span class="sxs-lookup"><span data-stu-id="7a54c-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (Visual Basic)](example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="7a54c-115">No seguinte documento, o primeiro parágrafo tem o estilo `Heading1`.</span><span class="sxs-lookup"><span data-stu-id="7a54c-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="7a54c-116">Há um número de parágrafos que têm o estilo padrão.</span><span class="sxs-lookup"><span data-stu-id="7a54c-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="7a54c-117">Há também um número de parágrafos que têm o estilo `Code`.</span><span class="sxs-lookup"><span data-stu-id="7a54c-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="7a54c-118">Devido a essa complexidade relativa, este é um documento mais interessante para analisar com LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="7a54c-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="7a54c-119">Naqueles parágrafos com estilos não padrão, elementos de parágrafo têm um elemento filho chamado `w:pPr`, que tem por sua vez contém um elemento filho `w:pStyle`.</span><span class="sxs-lookup"><span data-stu-id="7a54c-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="7a54c-120">Esse elemento tem um atributo, `w:val`, que contém o nome do estilo.</span><span class="sxs-lookup"><span data-stu-id="7a54c-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="7a54c-121">Se o parágrafo tem o estilo padrão, isso significa que o elemento de parágrafo não tiver um elemento filho de `w:p.Pr` .</span><span class="sxs-lookup"><span data-stu-id="7a54c-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a54c-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="7a54c-122">See also</span></span>

- [<span data-ttu-id="7a54c-123">Detalhes dos documentos do Office Open XML WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a54c-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](details-of-office-open-xml-wordprocessingml-documents.md)
