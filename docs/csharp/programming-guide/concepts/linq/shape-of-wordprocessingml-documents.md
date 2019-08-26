---
title: Formato de documentos de WordprocessingML (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 84d893267c37ecf99a457ebb683d0451e2b4b68f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591048"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="154fc-102">Formato de documentos de WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="154fc-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="154fc-103">Este tópico apresenta a forma XML de um documento WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="154fc-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="154fc-104">Formatos do Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="154fc-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="154fc-105">O formato de arquivo nativo para o sistema do Microsoft Office 2007 é Office Open XML (geralmente chamado de Open XML).</span><span class="sxs-lookup"><span data-stu-id="154fc-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="154fc-106">O Open XML é um formato baseado em XML que tem um padrão Ecma e está no momento passando por um processo de padrões de ISO-IEC.</span><span class="sxs-lookup"><span data-stu-id="154fc-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="154fc-107">A linguagem de marcação para arquivos de processamento de texto dentro do Open XML é chamada de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="154fc-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="154fc-108">Este tutorial usa arquivos de origem do WordprocessingML como entrada para os exemplos.</span><span class="sxs-lookup"><span data-stu-id="154fc-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="154fc-109">Se você estiver usando o Microsoft Office 2003, pode salvar documentos no formato Office Open XML se instalou os formatos de arquivo do Pacote de compatibilidade do Microsoft Office para Word, Excel e PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="154fc-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="154fc-110">O formato de documentos de WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="154fc-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="154fc-111">A primeira coisa a entender é a forma dos documentos de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="154fc-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="154fc-112">Um documento de WordprocessingML contém um elemento do corpo (chamado `w:body`) que contém os parágrafos do documento.</span><span class="sxs-lookup"><span data-stu-id="154fc-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="154fc-113">Cada parágrafo contém uma ou mais execuções de texto (chamado `w:r`).</span><span class="sxs-lookup"><span data-stu-id="154fc-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="154fc-114">Cada execução de texto contém uma ou mais partes de texto (chamado `w:t`).</span><span class="sxs-lookup"><span data-stu-id="154fc-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="154fc-115">Veja a seguir um documento muito simples de WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="154fc-115">The following is a very simple WordprocessingML document:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
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
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 <span data-ttu-id="154fc-116">Este documento contém dois parágrafos.</span><span class="sxs-lookup"><span data-stu-id="154fc-116">This document contains two paragraphs.</span></span> <span data-ttu-id="154fc-117">Ambos contêm uma única execução de texto, e cada execução de texto contém uma única parte de texto.</span><span class="sxs-lookup"><span data-stu-id="154fc-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="154fc-118">A maneira mais fácil para ver o conteúdo de um documento de WordprocessingML no formato XML é criar um usando Microsoft Word, salvá-lo e executar o seguinte programa que lê XML no console.</span><span class="sxs-lookup"><span data-stu-id="154fc-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="154fc-119">Este exemplo usa as classes encontradas no assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="154fc-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="154fc-120">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="154fc-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="154fc-121">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="154fc-121">External Resources</span></span>  
 [<span data-ttu-id="154fc-122">Apresentando os formatos de arquivo do Office (2007) Open XML</span><span class="sxs-lookup"><span data-stu-id="154fc-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)  
 [<span data-ttu-id="154fc-123">Visão geral de WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="154fc-123">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)  
 [<span data-ttu-id="154fc-124">Anatomia de um arquivo de WordProcessingML</span><span class="sxs-lookup"><span data-stu-id="154fc-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)  
 [<span data-ttu-id="154fc-125">Introdução a WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="154fc-125">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [<span data-ttu-id="154fc-126">Office 2003: página de download de esquemas de referência de XML</span><span class="sxs-lookup"><span data-stu-id="154fc-126">Office 2003: XML Reference Schemas Download page</span></span>](https://www.microsoft.com/download/details.aspx?id=101)  
  
## <a name="see-also"></a><span data-ttu-id="154fc-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="154fc-127">See also</span></span>

- [<span data-ttu-id="154fc-128">Tutorial: manipulando conteúdo em um documento WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="154fc-128">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
