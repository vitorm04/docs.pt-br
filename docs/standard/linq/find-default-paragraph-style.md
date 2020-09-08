---
title: Localizar o estilo de parágrafo padrão-LINQ to XML
description: Saiba como localizar o estilo padrão de parágrafos em um documento do WordprocessingML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 0e66856a551410dd488148ff678b684489396d62
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551845"
---
# <a name="find-the-default-paragraph-style-linq-to-xml"></a><span data-ttu-id="829d8-103">Localizar o estilo de parágrafo padrão (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="829d8-103">Find the default paragraph style (LINQ to XML)</span></span>

<span data-ttu-id="829d8-104">A primeira tarefa no [tutorial: manipular o conteúdo em um documento do WordprocessingML](xml-shape-wordprocessingml-documents.md) é encontrar o estilo padrão dos parágrafos no documento.</span><span class="sxs-lookup"><span data-stu-id="829d8-104">The first task in [Tutorial: Manipulate content in a WordprocessingML document](xml-shape-wordprocessingml-documents.md) is to find the default style of paragraphs in the document.</span></span>

## <a name="example-find-the-default-style-name"></a><span data-ttu-id="829d8-105">Exemplo: localizar o nome do estilo padrão</span><span class="sxs-lookup"><span data-stu-id="829d8-105">Example: Find the default style name</span></span>

<span data-ttu-id="829d8-106">O exemplo a seguir abre um documento do Office Open XML WordprocessingML, encontrar as partes do documento e estilo de pacote em seguida, executa uma consulta que localize o nome padrão de estilo.</span><span class="sxs-lookup"><span data-stu-id="829d8-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="829d8-107">Para obter informações sobre pacotes de documentos XML abertos do Office e as partes que compõem, consulte [detalhes dos documentos do Office Open XML WordprocessingML](wordprocessingml-document-styles.md).</span><span class="sxs-lookup"><span data-stu-id="829d8-107">For information about Office Open XML document packages, and the parts they comprise, see [Details of Office Open XML WordprocessingML documents](wordprocessingml-document-styles.md).</span></span>

<span data-ttu-id="829d8-108">A consulta encontrar um nó chamado `w:style` que tem um atributo chamado `w:type` com um valor de “parágrafo”, e também tem um atributo chamado `w:default` com um valor de “1 ".</span><span class="sxs-lookup"><span data-stu-id="829d8-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="829d8-109">Haverá porque apenas um nó XML com esses atributos, a consulta usa o operador de <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> para converter uma coleção para um único.</span><span class="sxs-lookup"><span data-stu-id="829d8-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="829d8-110">Então obtém o valor do atributo com o nome `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="829d8-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>

<span data-ttu-id="829d8-111">Este exemplo usa classes do assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="829d8-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="829d8-112">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="829d8-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

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

// The following query finds all the paragraphs that have the default style.
string defaultStyle =
    (string)(
        from style in styleDoc.Root.Elements(w + "style")
        where (string)style.Attribute(w + "type") == "paragraph"&&
              (string)style.Attribute(w + "default") == "1"
              select style
    ).First().Attribute(w + "styleId");

Console.WriteLine("The default style is: {0}", defaultStyle);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1

    Sub Main()

        Const fileName As String = "SampleDoc.docx"

        Const documentRelationshipType As String = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Const stylesRelationshipType As String = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"

        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing

        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = _
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If docPackageRelationship IsNot Nothing Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _
                  docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                ' Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                ' Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = _
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If styleRelation IsNot Nothing Then
                    Dim styleUri As Uri = _
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)

                    ' Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))
                End If
            End If
        End Using

        ' The following query finds all the paragraphs that have the default style.
        Dim defParas As IEnumerable(Of XElement) = _
            From style In styleDoc.Root.<w:style> _
            Where style.@w:type.Equals("paragraph") And _
                   style.@w:default.Equals("1") _
            Select style
        ' Then find the style of the first.
        Dim defaultStyle As String = defParas.First().@w:styleId

        Console.WriteLine("The default style is: " & defaultStyle)
    End Sub
End Module
```

<span data-ttu-id="829d8-113">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="829d8-113">This example produces the following output:</span></span>

```output
The default style is: Normal
```

<span data-ttu-id="829d8-114">No próximo artigo deste tutorial, você criará uma consulta semelhante que localiza todos os parágrafos em um documento e seus estilos:</span><span class="sxs-lookup"><span data-stu-id="829d8-114">In the next article in this tutorial you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>

- [<span data-ttu-id="829d8-115">Recuperar os parágrafos e seus estilos</span><span class="sxs-lookup"><span data-stu-id="829d8-115">Retrieve the paragraphs and their styles</span></span>](retrieve-paragraphs-styles.md)

## <a name="see-also"></a><span data-ttu-id="829d8-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="829d8-116">See also</span></span>

- [<span data-ttu-id="829d8-117">Tutorial: manipular conteúdo em um documento do WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="829d8-117">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
