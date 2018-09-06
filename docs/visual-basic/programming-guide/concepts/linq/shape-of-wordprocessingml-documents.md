---
title: Forma de documentos de WordprocessingML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 30ec7a0c6b03d0c6f00561ce08cb836aab3c167b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777636"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="63e07-102">Forma de documentos de WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63e07-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="63e07-103">Este tópico apresenta a forma XML de um documento WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="63e07-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="63e07-104">Formatos do Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="63e07-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="63e07-105">O formato de arquivo nativo para o sistema do Microsoft Office 2007 é Office Open XML (geralmente chamado de Open XML).</span><span class="sxs-lookup"><span data-stu-id="63e07-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="63e07-106">O Open XML é um formato baseado em XML que tem um padrão Ecma e está no momento passando por um processo de padrões de ISO-IEC.</span><span class="sxs-lookup"><span data-stu-id="63e07-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="63e07-107">A linguagem de marcação para arquivos de processamento de texto dentro do Open XML é chamada de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="63e07-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="63e07-108">Este tutorial usa arquivos de origem do WordprocessingML como entrada para os exemplos.</span><span class="sxs-lookup"><span data-stu-id="63e07-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="63e07-109">Se você estiver usando o Microsoft Office 2003, pode salvar documentos no formato Office Open XML se instalou os formatos de arquivo do Pacote de compatibilidade do Microsoft Office para Word, Excel e PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="63e07-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="63e07-110">O formato de documentos de WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="63e07-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="63e07-111">A primeira coisa a entender é a forma dos documentos de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="63e07-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="63e07-112">Um documento de WordprocessingML contém um elemento do corpo (chamado `w:body`) que contém os parágrafos do documento.</span><span class="sxs-lookup"><span data-stu-id="63e07-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="63e07-113">Cada parágrafo contém uma ou mais execuções de texto (chamado `w:r`).</span><span class="sxs-lookup"><span data-stu-id="63e07-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="63e07-114">Cada execução de texto contém uma ou mais partes de texto (chamado `w:t`).</span><span class="sxs-lookup"><span data-stu-id="63e07-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="63e07-115">Veja a seguir um documento muito simples de WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="63e07-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="63e07-116">Este documento contém dois parágrafos.</span><span class="sxs-lookup"><span data-stu-id="63e07-116">This document contains two paragraphs.</span></span> <span data-ttu-id="63e07-117">Ambos contêm uma única execução de texto, e cada execução de texto contém uma única parte de texto.</span><span class="sxs-lookup"><span data-stu-id="63e07-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="63e07-118">A maneira mais fácil para ver o conteúdo de um documento de WordprocessingML no formato XML é criar um usando Microsoft Word, salvá-lo e executar o seguinte programa que lê XML no console.</span><span class="sxs-lookup"><span data-stu-id="63e07-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="63e07-119">Este exemplo usa as classes encontradas no assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="63e07-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="63e07-120">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="63e07-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="63e07-121">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="63e07-121">External Resources</span></span>  
 <span data-ttu-id="63e07-122">[Apresentando os formatos de arquivo do Office (2007) Open XML](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span><span class="sxs-lookup"><span data-stu-id="63e07-122">[Introducing the Office (2007) Open XML File Formats](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span></span>  
  
 <span data-ttu-id="63e07-123">[Visão geral de WordprocessingML](https://msdn.microsoft.com/en-us/library/aa212812(office.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="63e07-123">[Overview of WordprocessingML](https://msdn.microsoft.com/en-us/library/aa212812(office.11).aspx)</span></span>  
  
 [<span data-ttu-id="63e07-124">Office 2003: página de download de esquemas de referência XML</span><span class="sxs-lookup"><span data-stu-id="63e07-124">Office 2003: XML Reference Schemas Download page</span></span>](https://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a><span data-ttu-id="63e07-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63e07-125">See Also</span></span>  
 [<span data-ttu-id="63e07-126">Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63e07-126">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
