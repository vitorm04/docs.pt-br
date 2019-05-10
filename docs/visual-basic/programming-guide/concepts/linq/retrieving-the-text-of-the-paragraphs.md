---
title: Recuperando o texto dos parágrafos (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: f508c95d5ea7889d3ea22a4852b4813ec54f97a1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627159"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a><span data-ttu-id="f7622-102">Recuperando o texto dos parágrafos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7622-102">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>
<span data-ttu-id="f7622-103">Este exemplo se baseia no exemplo anterior, [recuperando os parágrafos e seus estilos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="f7622-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="f7622-104">Esse novo exemplo recupera o texto de cada parágrafo como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f7622-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="f7622-105">Para recuperar o texto, este exemplo adiciona uma consulta adicional que executa iterações através da coleção de tipos anônimos e projeta uma nova coleção de um tipo anônimo com a adição de um novo membro, `Text`.</span><span class="sxs-lookup"><span data-stu-id="f7622-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="f7622-106">Usa o operador padrão de consulta de <xref:System.Linq.Enumerable.Aggregate%2A> para concatenar várias cadeias de caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f7622-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="f7622-107">Essa técnica (isto é, principalmente se projetando a uma coleção de um tipo anônimo, usando nessa coleção para se a projetar uma nova coleção de um tipo anônimo) é uma linguagem comum e útil.</span><span class="sxs-lookup"><span data-stu-id="f7622-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="f7622-108">Esta consulta pode ter sido gravados sem projeto para o primeiro tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="f7622-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="f7622-109">Entretanto, por causa da avaliação lazy, fazer isso não usa de poder de processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="f7622-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="f7622-110">O idioma cria um breves mais objetos na heap, mas isso não prejudica significativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="f7622-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="f7622-111">Naturalmente, seria possível escrever uma única consulta que contém a funcionalidade para recuperar os parágrafos, o estilo de cada parágrafo, e o texto de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="f7622-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="f7622-112">No entanto, geralmente é útil dividir uma consulta mais complexa em consultas múltiplas porque o código resultante é mais modular e fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="f7622-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="f7622-113">Além disso, se você precisar de reutilizar parte de consulta, é mais fácil refatorar se as consultas são gravadas dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="f7622-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="f7622-114">Essas consultas, que são encadeadas, usam o modelo de processamento que é examinado em detalhes no tópico [Tutorial: (Visual Basic) de execução adiada](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).</span><span class="sxs-lookup"><span data-stu-id="f7622-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Deferred Execution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7622-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7622-115">Example</span></span>  
 <span data-ttu-id="f7622-116">Este exemplo processa um documento de WordprocessingML, determinando o nó do elemento, o nome do estilo, e o texto de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="f7622-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="f7622-117">Este exemplo cria nos exemplos anteriores neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="f7622-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="f7622-118">A nova consulta é chamada nos comentários no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f7622-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="f7622-119">Para obter instruções para criar o documento de origem para este exemplo, consulte [criando o código-fonte Office documento Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="f7622-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="f7622-120">Este exemplo usa classes do assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="f7622-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="f7622-121">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7622-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    ' Following function is required because VB does not support short circuit evaluation  
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
  
 <span data-ttu-id="f7622-122">Este exemplo produz a seguinte saída quando aplicado ao documento descrito em [criando o código-fonte Office documento Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="f7622-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
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
  
## <a name="next-steps"></a><span data-ttu-id="f7622-123">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f7622-123">Next Steps</span></span>  
 <span data-ttu-id="f7622-124">O exemplo a seguir mostra como usar um método de extensão, em vez de <xref:System.Linq.Enumerable.Aggregate%2A>, para concatenar várias cadeias de caracteres em uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f7622-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="f7622-125">Refatoração usando um método de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7622-125">Refactoring Using an Extension Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="f7622-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7622-126">See also</span></span>

- [<span data-ttu-id="f7622-127">Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7622-127">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="f7622-128">Execução adiada e avaliação lenta em LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7622-128">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
