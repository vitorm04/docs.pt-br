---
title: Recuperar o texto dos parágrafos-LINQ to XML
description: Saiba como localizar os nós de parágrafo em um documento do WordprocessingML e recuperar o texto de cada nó como uma cadeia de caracteres.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: f41e0206f91f022993ed2c48681f124bf84ec603
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552056"
---
# <a name="retrieve-the-text-of-the-paragraphs-linq-to-xml"></a><span data-ttu-id="cfcea-103">Recuperar o texto dos parágrafos (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cfcea-103">Retrieve the text of the paragraphs (LINQ to XML)</span></span>

<span data-ttu-id="cfcea-104">Este exemplo baseia-se no exemplo anterior, [recupera os parágrafos e seus estilos](retrieve-paragraphs-styles.md).</span><span class="sxs-lookup"><span data-stu-id="cfcea-104">This example builds on the previous example, [Retrieve the paragraphs and their styles](retrieve-paragraphs-styles.md).</span></span> <span data-ttu-id="cfcea-105">Esse novo exemplo recupera o texto de cada parágrafo como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="cfcea-105">This new example retrieves the text of each paragraph as a string.</span></span>

<span data-ttu-id="cfcea-106">Para recuperar o texto, este exemplo adiciona uma consulta adicional que executa iterações através da coleção de tipos anônimos e projeta uma nova coleção de um tipo anônimo com a adição de um novo membro, `Text`.</span><span class="sxs-lookup"><span data-stu-id="cfcea-106">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="cfcea-107">Usa o operador padrão de consulta de <xref:System.Linq.Enumerable.Aggregate%2A> para concatenar várias cadeias de caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="cfcea-107">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>

<span data-ttu-id="cfcea-108">Essa técnica (ou seja, o primeiro projeto para uma coleção de um tipo anônimo, usando essa coleção para projetar em uma nova coleção de um tipo anônimo) é comum e útil.</span><span class="sxs-lookup"><span data-stu-id="cfcea-108">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful one.</span></span> <span data-ttu-id="cfcea-109">Esta consulta pode ter sido gravados sem projeto para o primeiro tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="cfcea-109">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="cfcea-110">No entanto, devido à avaliação lenta, fazer isso não usa muita capacidade de processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="cfcea-110">However, because of lazy evaluation, doing so doesn't use much additional processing power.</span></span> <span data-ttu-id="cfcea-111">A técnica cria mais objetos de curta duração no heap, mas isso não prejudica substancialmente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="cfcea-111">The technique does create more short-lived objects on the heap, but that doesn't substantially degrade performance.</span></span>

<span data-ttu-id="cfcea-112">Naturalmente, seria possível escrever uma única consulta que contém a funcionalidade para recuperar os parágrafos, o estilo de cada parágrafo, e o texto de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="cfcea-112">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="cfcea-113">No entanto, geralmente é útil dividir uma consulta mais complicada em várias consultas porque o código resultante é mais modular e mais fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="cfcea-113">However, it's often useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="cfcea-114">Além disso, se você precisar reutilizar uma parte da consulta, será mais fácil refatorar se as consultas forem gravadas dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="cfcea-114">Further, if you need to reuse a portion of the query, it's easier to refactor if the queries are written in this manner.</span></span>

<span data-ttu-id="cfcea-115">Essas consultas, que são encadeadas, usam o modelo de processamento examinado no [exemplo de consultas de encadeamento](chain-queries-example.md)de artigo.</span><span class="sxs-lookup"><span data-stu-id="cfcea-115">These queries, which are chained together, use the processing model that's examined in the article [Chain queries example](chain-queries-example.md).</span></span>

## <a name="example-determine-the-element-node-style-name-and-text-of-each-paragraph"></a><span data-ttu-id="cfcea-116">Exemplo: determinar o nó do elemento, o nome do estilo e o texto de cada parágrafo</span><span class="sxs-lookup"><span data-stu-id="cfcea-116">Example: Determine the element node, style name, and text of each paragraph</span></span>

<span data-ttu-id="cfcea-117">Este exemplo processa um documento do WordprocessingML, determinando o nó do elemento, o nome do estilo e o texto de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="cfcea-117">This example processes a WordprocessingML document, determining the element node, style name, and text of each paragraph.</span></span> <span data-ttu-id="cfcea-118">Este exemplo cria nos exemplos anteriores neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="cfcea-118">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="cfcea-119">A nova consulta é chamada nos comentários no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="cfcea-119">The new query is called out in comments in the code below.</span></span>

<span data-ttu-id="cfcea-120">As instruções para criar o documento de origem para este exemplo estão em [criar o documento Office Open XML de origem](create-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="cfcea-120">The instructions for creating the source document for this example are in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="cfcea-121">Este exemplo usa classes do assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="cfcea-121">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="cfcea-122">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cfcea-122">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```csharp
const string fileName = "SampleDoc.docx";

const string documentRelationshipType =
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";
const string stylesRelationshipType =
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";
const string wordmlNamespace =
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";
XNamespace w = wordmlNamespace;

XDocument xDoc = null;
XDocument styleDoc = null;

using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))
{
    PackageRelationship docPackageRelationship =
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();
    if (docPackageRelationship != null)
    {
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),
          docPackageRelationship.TargetUri);
        PackagePart documentPart = wdPackage.GetPart(documentUri);

        //  Load the document XML in the part into an XDocument instance.
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

        //  Find the styles part. There will only be one.
        PackageRelationship styleRelation =
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();
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

// Find all paragraphs in the document.
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

// Following is the new query that retrieves the text of
// each paragraph.
var paraWithText =
    from para in paragraphs
    select new
    {
        ParagraphNode = para.ParagraphNode,
        StyleName = para.StyleName,
        Text = para
               .ParagraphNode
               .Elements(w + "r")
               .Elements(w + "t")
               .Aggregate(
                   new StringBuilder(),
                   (s, i) => s.Append((string)i),
                   s => s.ToString()
               )
    };

foreach (var p in paraWithText)
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    ' Following function is required because Visual Basic doesn't support short circuit evaluation
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _
                                         ByVal defaultStyle As String) As String
        If (styleNode Is Nothing) Then
            Return defaultStyle
        Else
            Return styleNode.@w:val
        End If
    End Function

    Sub Main()
        Dim fileName = "SampleDoc.docx"

        Dim documentRelationshipType = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Dim stylesRelationshipType = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"
        Dim wordmlNamespace = _
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"

        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = _
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _
                  docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = _
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If (styleRelation IsNot Nothing) Then
                    Dim styleUri As Uri = _
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
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

        ' Find all paragraphs in the document.
        Dim paragraphs = _
            From para In xDoc.Root.<w:body>...<w:p> _
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _
        Select New With { _
            .ParagraphNode = para, _
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _
        }

        ' Following is the new query that retrieves the text of
        ' each paragraph.
        Dim paraWithText = _
            From para In paragraphs _
            Select New With { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = para.ParagraphNode.<w:r>.<w:t> _
                    .Aggregate(New StringBuilder(), _
                               Function(s As StringBuilder, i As String) s.Append(CStr(i)), _
                               Function(s As StringBuilder) s.ToString) _
            }

        For Each p In paraWithText
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)
        Next

    End Sub
End Module
```

<span data-ttu-id="cfcea-123">A versão em C# deste exemplo produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="cfcea-123">The C# version of this example produces the following output:</span></span>

```conssole
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<
StyleName:Normal ><
StyleName:Normal >The following example prints to the console.<
StyleName:Normal ><
StyleName:Code >using System;<
StyleName:Code ><
StyleName:Code >class Program {<
StyleName:Code >    public static void (string[] args) {<
StyleName:Code >        Console.WriteLine("Hello World");<
StyleName:Code >    }<
StyleName:Code >}<
StyleName:Normal ><
StyleName:Normal >This example produces the following output:<
StyleName:Normal ><
StyleName:Code >Hello World<
```

<span data-ttu-id="cfcea-124">A versão Visual Basic deste exemplo produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="cfcea-124">The Visual Basic version of this example produces the following output:</span></span>

```output
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<
StyleName:Normal ><
StyleName:Normal >The following example prints to the console.<
StyleName:Normal ><
StyleName:Code >Imports System<
StyleName:Code ><
StyleName:Code >Class Program<
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<
StyleName:Code >        Console.WriteLine("Hello World")<
StyleName:Code >   End Sub<
StyleName:Code >End Class<
StyleName:Normal ><
StyleName:Normal >This example produces the following output:<
StyleName:Normal ><
StyleName:Code >Hello World<
```

<span data-ttu-id="cfcea-125">O próximo artigo deste tutorial mostra como usar um método de extensão, em vez de <xref:System.Linq.Enumerable.Aggregate%2A> , para concatenar várias cadeias de caracteres em uma única cadeia:</span><span class="sxs-lookup"><span data-stu-id="cfcea-125">The next article in this tutorial shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string:</span></span>

- [<span data-ttu-id="cfcea-126">Refatorar usando um método de extensão</span><span class="sxs-lookup"><span data-stu-id="cfcea-126">Refactor using an extension method</span></span>](refactor-extension-method.md)

## <a name="see-also"></a><span data-ttu-id="cfcea-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="cfcea-127">See also</span></span>

- [<span data-ttu-id="cfcea-128">Tutorial: manipular conteúdo em um documento do WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="cfcea-128">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
- [<span data-ttu-id="cfcea-129">Execução retardada e avaliação lenta</span><span class="sxs-lookup"><span data-stu-id="cfcea-129">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
