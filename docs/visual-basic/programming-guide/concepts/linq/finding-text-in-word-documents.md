---
title: Localizando texto em documentos do Word (Visual Basic)
ms.date: 07/20/2015
ms.assetid: eea9819b-a78a-4552-bf13-8837fc0e7a37
ms.openlocfilehash: f8414662e2013b152e471d6c4c003e602c0d277d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814361"
---
# <a name="finding-text-in-word-documents-visual-basic"></a><span data-ttu-id="a5799-102">Localizando texto em documentos do Word (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5799-102">Finding Text in Word Documents (Visual Basic)</span></span>
<span data-ttu-id="a5799-103">Este tópico estende as consultas anteriores para fazer algo útil: localizar todas as ocorrências de uma cadeia de caracteres no documento.</span><span class="sxs-lookup"><span data-stu-id="a5799-103">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5799-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5799-104">Example</span></span>  
 <span data-ttu-id="a5799-105">Este exemplo processa um documento de WordprocessingML para localizar todas as ocorrências de uma parte específica de texto no documento.</span><span class="sxs-lookup"><span data-stu-id="a5799-105">This example processes a WordprocessingML document, to find all the occurrences of a specific piece of text in the document.</span></span> <span data-ttu-id="a5799-106">Para fazer isso, usamos uma consulta encontrar a cadeia de caracteres “hello world”.</span><span class="sxs-lookup"><span data-stu-id="a5799-106">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="a5799-107">Este exemplo cria nos exemplos anteriores neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="a5799-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="a5799-108">A nova consulta é chamada nos comentários no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5799-108">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="a5799-109">Para obter instruções para criar o documento de origem para este exemplo, consulte [criando o código-fonte Office documento Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="a5799-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="a5799-110">Este exemplo usa as classes encontradas no assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="a5799-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="a5799-111">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a5799-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As String In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    Public Function ParagraphText(ByVal e As XElement) As String  
        Dim w As XNamespace = e.Name.Namespace  
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))  
    End Function  
  
    ' Following function is required because VB does not support short circuit evaluation  
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
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Retrieve the text of each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = ParagraphText(para.ParagraphNode) _  
            }  
  
        ' Following is the new query that retrieves all paragraphs  
        ' that have specific text in them.  
        Dim helloParagraphs = _  
            From para In paraWithText _  
            Where para.Text.Contains("Hello") _  
            Select New With _  
            { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.Text _  
            }  
  
        For Each p In helloParagraphs  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="a5799-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a5799-112">This example produces the following output:</span></span>  
  
```  
StyleName:Code >        Console.WriteLine("Hello World")<  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="a5799-113">Você pode, é claro, altere a pesquisa para que procura por linhas com um determinado estilo.</span><span class="sxs-lookup"><span data-stu-id="a5799-113">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="a5799-114">A consulta a seguir localiza todas as linhas em branco que têm o estilo de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a5799-114">The following query finds all blank lines that have the Code style:</span></span>  
  
```vb  
Imports System.IO.Packaging  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As String In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    Public Function ParagraphText(ByVal e As XElement) As String  
        Dim w As XNamespace = e.Name.Namespace  
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))  
    End Function  
  
    ' Following function is required because VB does not support short circuit evaluation  
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
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Retrieve the text of each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = ParagraphText(para.ParagraphNode) _  
            }  
  
        ' Retrieve all paragraphs that have no text and are styled Code.  
        Dim blankCodeParagraphs = _  
            From para In paraWithText _  
            Where String.IsNullOrEmpty(para.Text) And para.StyleName.Equals("Code") _  
            Select New With _  
            { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.Text _  
            }  
  
        For Each p In blankCodeParagraphs  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="a5799-115">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a5799-115">This example produces the following output:</span></span>  
  
```  
StyleName:Code ><  
```  
  
 <span data-ttu-id="a5799-116">Naturalmente, este exemplo pode ser aprimorado de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="a5799-116">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="a5799-117">Por exemplo, nós poderíamos usar expressões regulares para procurar pelo texto, nós poderíamos iterar através de todos os arquivos do Word em um diretório específico, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a5799-117">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>  
  
 <span data-ttu-id="a5799-118">Observe que este exemplo reproduz funciona bem como se ele foi gravado como uma única consulta.</span><span class="sxs-lookup"><span data-stu-id="a5799-118">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="a5799-119">Porque cada consulta é implementada em um lenta, a forma adiada, cada consulta não produz resultados até que a consulta é iterada.</span><span class="sxs-lookup"><span data-stu-id="a5799-119">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="a5799-120">Para obter mais informações sobre a execução e avaliação lenta, consulte [execução adiada e avaliação lenta em LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a5799-120">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a5799-121">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a5799-121">Next Steps</span></span>  
 <span data-ttu-id="a5799-122">A próxima seção fornece informações sobre documentos de WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="a5799-122">The next section provides more information about WordprocessingML documents:</span></span>  
  
-   [<span data-ttu-id="a5799-123">Detalhes do Office Open XML WordprocessingML documentos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5799-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)  
  
## <a name="see-also"></a><span data-ttu-id="a5799-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5799-124">See also</span></span>

- [<span data-ttu-id="a5799-125">Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5799-125">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="a5799-126">Refatoração usando uma função pura (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5799-126">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)
- [<span data-ttu-id="a5799-127">Execução adiada e avaliação lenta em LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5799-127">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
