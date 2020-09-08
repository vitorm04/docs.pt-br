---
title: Recuperar os parágrafos e seus estilos-LINQ to XML
description: Saiba como recuperar nós de parágrafo e seus estilos de um documento do WordprocessingML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 43c6173441dda841236a4397e28d0bb2c7c8d003
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552064"
---
# <a name="retrieve-the-paragraphs-and-their-styles-linq-to-xml"></a><span data-ttu-id="dd7cd-103">Recuperar os parágrafos e seus estilos (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="dd7cd-103">Retrieve the paragraphs and their styles (LINQ to XML)</span></span>

<span data-ttu-id="dd7cd-104">Nesse exemplo, nós escrevemos uma consulta que recupera os nós de parágrafo de um documento de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-104">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="dd7cd-105">Também identifica o estilo de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-105">It also identifies the style of each paragraph.</span></span>

<span data-ttu-id="dd7cd-106">Essa consulta se baseia na consulta no exemplo anterior, [localize o estilo de parágrafo padrão](find-default-paragraph-style.md), que recupera o estilo padrão da lista de estilos.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-106">This query builds on the query in the previous example, [Find the default paragraph style](find-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="dd7cd-107">Essas informações são necessárias para que a consulta possa identificar o estilo dos parágrafos que não têm um estilo explicitamente definido.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-107">This information is required so that the query can identify the style of paragraphs that don't have a style explicitly set.</span></span> <span data-ttu-id="dd7cd-108">Os estilos de parágrafo são definidos por meio do `w:pPr` elemento; se um parágrafo não contiver esse elemento, ele será formatado com o estilo padrão.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-108">Paragraph styles are set through the `w:pPr` element; if a paragraph doesn't contain this element, it's formatted with the default style.</span></span>

<span data-ttu-id="dd7cd-109">Este artigo explica a significância de algumas partes da consulta e, em seguida, mostra a consulta como parte de um exemplo funcional completo.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-109">This article explains the significance of some pieces of the query, then shows the query as part of a complete working example.</span></span>

## <a name="example-retrieve-all-the-paragraphs-in-a-document-and-the-paragraph-styles"></a><span data-ttu-id="dd7cd-110">Exemplo: recuperar todos os parágrafos em um documento e os estilos de parágrafo</span><span class="sxs-lookup"><span data-stu-id="dd7cd-110">Example: Retrieve all the paragraphs in a document, and the paragraph styles</span></span>

<span data-ttu-id="dd7cd-111">O código a seguir é uma consulta para recuperar todos os parágrafos em um documento e seus estilos:</span><span class="sxs-lookup"><span data-stu-id="dd7cd-111">The following code is a query to retrieve all the paragraphs in a document and their styles:</span></span>

```csharp
xDoc.Root.Element(w + "body").Descendants(w + "p")
```

```vb
xDoc.Root.<w:body>...<w:p>
```

<span data-ttu-id="dd7cd-112">Essa expressão é semelhante à origem da consulta no exemplo anterior, [localizar o estilo de parágrafo padrão](find-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="dd7cd-112">This expression is similar to the source of the query in the previous example, [Find the default paragraph style](find-default-paragraph-style.md).</span></span> <span data-ttu-id="dd7cd-113">A principal diferença é que usa o eixo de <xref:System.Xml.Linq.XContainer.Descendants%2A> em vez do eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="dd7cd-113">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="dd7cd-114">A consulta usa o <xref:System.Xml.Linq.XContainer.Descendants%2A> eixo porque, em documentos que têm seções, os parágrafos não serão os filhos diretos do elemento body; em vez disso, os parágrafos serão dois níveis abaixo na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-114">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs won't be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="dd7cd-115">Usando o <xref:System.Xml.Linq.XContainer.Descendants%2A> eixo, o código funcionará se o documento usar ou não seções.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-115">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work whether or not the document uses sections.</span></span>

## <a name="example-use-a-let-clause-to-determine-the-element-that-contains-the-style-node"></a><span data-ttu-id="dd7cd-116">Exemplo: Use uma `let` cláusula para determinar o elemento que contém o nó de estilo</span><span class="sxs-lookup"><span data-stu-id="dd7cd-116">Example: Use a `let` clause to determine the element that contains the style node</span></span>

<span data-ttu-id="dd7cd-117">A consulta a seguir usa uma `let` cláusula para determinar o elemento que contém o nó de estilo:</span><span class="sxs-lookup"><span data-stu-id="dd7cd-117">The following query uses a `let` clause to determine the element that contains the style node:</span></span>

```csharp
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()
```

 ```vb
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()
```

<span data-ttu-id="dd7cd-118">A `let` cláusula ( `Let` na versão Visual Basic) primeiro usa o <xref:System.Xml.Linq.XContainer.Elements%2A> eixo para localizar todos os elementos chamados `pPr` , em seguida, usa o <xref:System.Xml.Linq.Extensions.Elements%2A> método de extensão para localizar todos os elementos filho chamados `pStyle` e, por fim, usa o <xref:System.Linq.Enumerable.FirstOrDefault%2A> operador de consulta padrão para converter a coleção em um singleton.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-118">The `let` clause (`Let` in the Visual Basic version) first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="dd7cd-119">Se a coleção estiver vazia, `styleNode` será definida como `null` ( `Nothing` na versão Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="dd7cd-119">If the collection is empty, `styleNode` is set to `null` (`Nothing` in the Visual Basic version).</span></span> <span data-ttu-id="dd7cd-120">Este é um idioma útil para procurar o nó descendente de `pStyle` .</span><span class="sxs-lookup"><span data-stu-id="dd7cd-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="dd7cd-121">Observe que, se o `pPr` nó filho não existir, o código não falhará lançando uma exceção; em vez disso, `styleNode` será definido como `null` ( `Nothing` ), que é o comportamento desejado dessa `let` `Let` cláusula ().</span><span class="sxs-lookup"><span data-stu-id="dd7cd-121">Note that if the `pPr` child node doesn't exist, the code doesn't fail by throwing an exception; instead, `styleNode` is set to `null` (`Nothing`), which is the desired behavior of this `let`(`Let`) clause.</span></span>

<span data-ttu-id="dd7cd-122">Se não houver nenhum elemento, `styleNode` será definido como `null` ( `Nothing` ).</span><span class="sxs-lookup"><span data-stu-id="dd7cd-122">If there is no element, then `styleNode` is set to `null` (`Nothing`).</span></span>

<span data-ttu-id="dd7cd-123">A consulta em uma coleção de um tipo anônimo com dois membros, `StyleName` e `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-123">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>

## <a name="example-retrieve-the-paragraph-nodes-from-a-wordprocessingml-document"></a><span data-ttu-id="dd7cd-124">Exemplo: recuperar os nós de parágrafo de um documento do WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="dd7cd-124">Example: Retrieve the paragraph nodes from a WordprocessingML document</span></span>

<span data-ttu-id="dd7cd-125">Este exemplo processa um documento do WordprocessingML, recuperando os nós de parágrafo.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-125">This example processes a WordprocessingML document, retrieving the paragraph nodes.</span></span> <span data-ttu-id="dd7cd-126">Também identifica o estilo de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-126">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="dd7cd-127">Este exemplo cria nos exemplos anteriores neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-127">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="dd7cd-128">A nova consulta é chamada nos comentários no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-128">The new query is called out in comments in the code below.</span></span>

<span data-ttu-id="dd7cd-129">As instruções para criar o documento de origem para este exemplo estão em [criar o documento Office Open XML de origem](create-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="dd7cd-129">The instructions for creating the source document for this example are in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="dd7cd-130">Este exemplo usa as classes encontradas no assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-130">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="dd7cd-131">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd7cd-131">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```csharp
const string fileName = "SampleDoc.docx";

const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";
const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";
const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";
XNamespace w = wordmlNamespace;

XDocument xDoc = null;
XDocument styleDoc = null;

using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))
{
    PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();
    if (docPackageRelationship != null)
    {
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);
        PackagePart documentPart = wdPackage.GetPart(documentUri);

        //  Load the document XML in the part into an XDocument instance.
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

        //  Find the styles part. There will only be one.
        PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();
        if (styleRelation != null)
        {
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);
            PackagePart stylePart = wdPackage.GetPart(styleUri);

            //  Load the style XML in the part into an XDocument instance.
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));
        }
    }
}

string defaultStyle =
    (string)(
        from style in styleDoc.Root.Elements(w + "style")
        where (string)style.Attribute(w + "type") == "paragraph"&&
              (string)style.Attribute(w + "default") == "1"
              select style
    ).First().Attribute(w + "styleId");

// Following is the new query that finds all paragraphs in the
// document and their styles.
var paragraphs =
    from para in xDoc
                 .Root
                 .Element(w + "body")
                 .Descendants(w + "p")
    let styleNode = para
                    .Elements(w + "pPr")
                    .Elements(w + "pStyle")
                    .FirstOrDefault()
    select new
    {
        ParagraphNode = para,
        StyleName = styleNode != null ?
            (string)styleNode.Attribute(w + "val") :
            defaultStyle
    };

foreach (var p in paragraphs)
    Console.WriteLine("StyleName:{0}", p.StyleName);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String
        If (styleNode Is Nothing) Then
            Return defaultStyle
        Else
            Return styleNode.@w:val
        End If
    End Function

    Sub Main()
        Dim fileName = "SampleDoc.docx"

        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"

        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If (styleRelation IsNot Nothing) Then
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)

                    '  Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))
                End If
            End If
        End Using

        Dim defaultStyle As String = _
            ( _
                From style In styleDoc.Root.<w:style> _
                Where style.@w:type = "paragraph" And _
                      style.@w:default = "1" _
                Select style _
            ).First().@w:styleId

        ' Following is the new query that finds all paragraphs in the
        ' document and their styles.
        Dim paragraphs = _
            From para In xDoc.Root.<w:body>...<w:p> _
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _
        Select New With { _
            .ParagraphNode = para, _
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _
        }

        For Each p In paragraphs
            Console.WriteLine("StyleName:{0}", p.StyleName)
        Next

    End Sub
End Module
```

<span data-ttu-id="dd7cd-132">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="dd7cd-132">This example produces the following output:</span></span>

```output
StyleName:Heading1
StyleName:Normal
StyleName:Normal
StyleName:Normal
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Normal
StyleName:Normal
StyleName:Normal
StyleName:Code
```

<span data-ttu-id="dd7cd-133">O próximo artigo deste tutorial mostra como criar uma consulta para recuperar o texto de parágrafos:</span><span class="sxs-lookup"><span data-stu-id="dd7cd-133">The next article in this tutorial shows how to create a query to retrieve the text of paragraphs:</span></span>

- [<span data-ttu-id="dd7cd-134">Recuperar o texto dos parágrafos</span><span class="sxs-lookup"><span data-stu-id="dd7cd-134">Retrieve the text of the paragraphs</span></span>](retrieve-text-paragraphs.md)

## <a name="see-also"></a><span data-ttu-id="dd7cd-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd7cd-135">See also</span></span>

- [<span data-ttu-id="dd7cd-136">Tutorial: manipular conteúdo em um documento do WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="dd7cd-136">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
