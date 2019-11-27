---
title: Localizar o estilo de parágrafo padrão
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: c3c92c7ae6f80082265d8516e62118595a341790
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353448"
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a><span data-ttu-id="4835a-102">Localizando o estilo de parágrafo padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4835a-102">Finding the Default Paragraph Style (Visual Basic)</span></span>
<span data-ttu-id="4835a-103">A primeira tarefa no tutorial Manipulando informações em um documento de WordprocessingML é localizar o estilo padrão dos parágrafos no documento.</span><span class="sxs-lookup"><span data-stu-id="4835a-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4835a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4835a-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4835a-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="4835a-105">Description</span></span>  
 <span data-ttu-id="4835a-106">O exemplo a seguir abre um documento do Office Open XML WordprocessingML, encontrar as partes do documento e estilo de pacote em seguida, executa uma consulta que localize o nome padrão de estilo.</span><span class="sxs-lookup"><span data-stu-id="4835a-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="4835a-107">Para obter informações sobre pacotes de documentos XML abertos do Office e as partes das quais eles consistem, consulte [detalhes dos documentos do Office Open XML WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="4835a-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="4835a-108">A consulta encontrar um nó chamado `w:style` que tem um atributo chamado `w:type` com um valor de “parágrafo”, e também tem um atributo chamado `w:default` com um valor de “1 ".</span><span class="sxs-lookup"><span data-stu-id="4835a-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="4835a-109">Haverá porque apenas um nó XML com esses atributos, a consulta usa o operador de <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> para converter uma coleção para um único.</span><span class="sxs-lookup"><span data-stu-id="4835a-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="4835a-110">Então obtém o valor do atributo com o nome `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="4835a-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="4835a-111">Este exemplo usa classes do assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="4835a-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="4835a-112">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4835a-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4835a-113">Código</span><span class="sxs-lookup"><span data-stu-id="4835a-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="4835a-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="4835a-114">Comments</span></span>  
 <span data-ttu-id="4835a-115">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="4835a-115">This example produces the following output:</span></span>  
  
```console  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="4835a-116">{1&gt;Próximas etapas&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4835a-116">Next Steps</span></span>  
 <span data-ttu-id="4835a-117">No exemplo a seguir, você criará uma consulta semelhante que localiza todos os parágrafos em um documento e seus estilos:</span><span class="sxs-lookup"><span data-stu-id="4835a-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="4835a-118">Recuperando os parágrafos e seus estilos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4835a-118">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="4835a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4835a-119">See also</span></span>

- [<span data-ttu-id="4835a-120">Tutorial: manipulando conteúdo em um documento do WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4835a-120">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
