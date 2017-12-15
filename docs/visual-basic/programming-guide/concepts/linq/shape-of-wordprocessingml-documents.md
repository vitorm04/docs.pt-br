---
title: Forma de documentos de WordprocessingML (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5809e8148e7ac426b876ad11948878ee0bfcd016
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2017
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="872a7-102">Forma de documentos de WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="872a7-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="872a7-103">Este tópico apresenta a forma XML de um documento WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="872a7-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="872a7-104">Formatos do Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="872a7-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="872a7-105">O formato de arquivo nativo para o sistema do Microsoft Office 2007 é Office Open XML (geralmente chamado de Open XML).</span><span class="sxs-lookup"><span data-stu-id="872a7-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="872a7-106">O Open XML é um formato baseado em XML que tem um padrão Ecma e está no momento passando por um processo de padrões de ISO-IEC.</span><span class="sxs-lookup"><span data-stu-id="872a7-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="872a7-107">A linguagem de marcação para arquivos de processamento de texto dentro do Open XML é chamada de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="872a7-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="872a7-108">Este tutorial usa arquivos de origem do WordprocessingML como entrada para os exemplos.</span><span class="sxs-lookup"><span data-stu-id="872a7-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="872a7-109">Se você estiver usando o Microsoft Office 2003, você pode salvar documentos no formato do Office Open XML, se você tiver instalado o pacote de compatibilidade do Microsoft Office para Word, Excel e formatos de arquivo do PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="872a7-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="872a7-110">O formato de documentos de WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="872a7-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="872a7-111">A primeira coisa a entender é a forma dos documentos de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="872a7-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="872a7-112">Um documento de WordprocessingML contém um elemento do corpo (chamado `w:body`) que contém os parágrafos do documento.</span><span class="sxs-lookup"><span data-stu-id="872a7-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="872a7-113">Cada parágrafo contém uma ou mais execuções de texto (chamado `w:r`).</span><span class="sxs-lookup"><span data-stu-id="872a7-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="872a7-114">Cada execução de texto contém uma ou mais partes de texto (chamado `w:t`).</span><span class="sxs-lookup"><span data-stu-id="872a7-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="872a7-115">Veja a seguir um documento muito simples de WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="872a7-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="872a7-116">Este documento contém dois parágrafos.</span><span class="sxs-lookup"><span data-stu-id="872a7-116">This document contains two paragraphs.</span></span> <span data-ttu-id="872a7-117">Ambos contêm uma única execução de texto, e cada execução de texto contém uma única parte de texto.</span><span class="sxs-lookup"><span data-stu-id="872a7-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="872a7-118">A maneira mais fácil para ver o conteúdo de um documento de WordprocessingML no formato XML é criar um usando Microsoft Word, salvá-lo e executar o seguinte programa que lê XML no console.</span><span class="sxs-lookup"><span data-stu-id="872a7-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="872a7-119">Este exemplo usa as classes encontradas no assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="872a7-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="872a7-120">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="872a7-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="872a7-121">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="872a7-121">External Resources</span></span>  
 [<span data-ttu-id="872a7-122">Apresentando os formatos de arquivo do Office (2007) Open XML</span><span class="sxs-lookup"><span data-stu-id="872a7-122">Introducing the Office (2007) Open XML File Formats</span></span>](http://go.microsoft.com/fwlink/?LinkId=98093)  
  
 [<span data-ttu-id="872a7-123">Visão geral de WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="872a7-123">Overview of WordprocessingML</span></span>](http://go.microsoft.com/fwlink/?LinkId=98094)  
  
 [<span data-ttu-id="872a7-124">Office 2003: página de download de esquemas de referência XML</span><span class="sxs-lookup"><span data-stu-id="872a7-124">Office 2003: XML Reference Schemas Download page</span></span>](http://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a><span data-ttu-id="872a7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="872a7-125">See Also</span></span>  
 [<span data-ttu-id="872a7-126">Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="872a7-126">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
