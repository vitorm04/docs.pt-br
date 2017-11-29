---
title: "Recuperando o texto dos parágrafos (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4d43ad0260406edac4920aad5f14c981de210b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="94086-102">Recuperando o texto dos parágrafos (C#)</span><span class="sxs-lookup"><span data-stu-id="94086-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="94086-103">Este exemplo é criado com base no exemplo anterior, [Recuperando os parágrafos e seus estilos (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="94086-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="94086-104">Esse novo exemplo recupera o texto de cada parágrafo como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="94086-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="94086-105">Para recuperar o texto, este exemplo adiciona uma consulta adicional que executa iterações através da coleção de tipos anônimos e projeta uma nova coleção de um tipo anônimo com a adição de um novo membro, `Text`.</span><span class="sxs-lookup"><span data-stu-id="94086-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="94086-106">Usa o operador padrão de consulta de <xref:System.Linq.Enumerable.Aggregate%2A> para concatenar várias cadeias de caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="94086-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="94086-107">Essa técnica (isto é, principalmente se projetando a uma coleção de um tipo anônimo, usando nessa coleção para se a projetar uma nova coleção de um tipo anônimo) é uma linguagem comum e útil.</span><span class="sxs-lookup"><span data-stu-id="94086-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="94086-108">Esta consulta pode ter sido gravados sem projeto para o primeiro tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="94086-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="94086-109">Entretanto, por causa da avaliação lazy, fazer isso não usa de poder de processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="94086-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="94086-110">O idioma cria um breves mais objetos na heap, mas isso não prejudica significativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="94086-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="94086-111">Naturalmente, seria possível escrever uma única consulta que contém a funcionalidade para recuperar os parágrafos, o estilo de cada parágrafo, e o texto de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="94086-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="94086-112">No entanto, geralmente é útil dividir uma consulta mais complexa em consultas múltiplas porque o código resultante é mais modular e fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="94086-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="94086-113">Além disso, se você precisar de reutilizar parte de consulta, é mais fácil refatorar se as consultas são gravadas dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="94086-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="94086-114">Essas consultas, que são encadeadas juntas, usam o modelo de processamento que é examinado em detalhes no tópico [Tutorial: encadear consultas juntas (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span><span class="sxs-lookup"><span data-stu-id="94086-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94086-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94086-115">Example</span></span>  
 <span data-ttu-id="94086-116">Este exemplo processa um documento de WordprocessingML, determinando o nó do elemento, o nome do estilo, e o texto de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="94086-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="94086-117">Este exemplo cria nos exemplos anteriores neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="94086-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="94086-118">A nova consulta é chamada nos comentários no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="94086-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="94086-119">Para obter instruções para criar o documento de origem deste exemplo, consulte [Criando o documento do Office Open XML de origem (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="94086-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="94086-120">Este exemplo usa classes do assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="94086-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="94086-121">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="94086-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="94086-122">Este exemplo produz a seguinte saída quando aplicado ao documento descrito em [Criando o documento do Office Open XML de origem (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="94086-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
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
  
## <a name="next-steps"></a><span data-ttu-id="94086-123">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="94086-123">Next Steps</span></span>  
 <span data-ttu-id="94086-124">O exemplo a seguir mostra como usar um método de extensão, em vez de <xref:System.Linq.Enumerable.Aggregate%2A>, para concatenar várias cadeias de caracteres em uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="94086-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
-   [<span data-ttu-id="94086-125">Refatoração usando um método de extensão (C#)</span><span class="sxs-lookup"><span data-stu-id="94086-125">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="94086-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94086-126">See Also</span></span>  
 [<span data-ttu-id="94086-127">Tutorial: manipulando conteúdo em um documento WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="94086-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [<span data-ttu-id="94086-128">Execução adiada e avaliação lenta em LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="94086-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
