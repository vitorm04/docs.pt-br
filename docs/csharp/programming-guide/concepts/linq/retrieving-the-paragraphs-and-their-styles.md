---
title: Recuperando os parágrafos e seus estilos (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 693c61e9cbf9e2027864da8d1c26e0a1af66094d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702412"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="65c42-102">Recuperando os parágrafos e seus estilos (C#)</span><span class="sxs-lookup"><span data-stu-id="65c42-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="65c42-103">Nesse exemplo, nós escrevemos uma consulta que recupera os nós de parágrafo de um documento de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="65c42-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="65c42-104">Também identifica o estilo de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="65c42-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="65c42-105">Esta consulta é baseada na consulta no exemplo anterior, [Localizando o estilo de parágrafo padrão (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), que recupera o estilo padrão da lista de estilos.</span><span class="sxs-lookup"><span data-stu-id="65c42-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="65c42-106">Essa informação é necessária de modo que a consulta pode identificar o estilo dos parágrafos que não têm um estilo definir explicitamente.</span><span class="sxs-lookup"><span data-stu-id="65c42-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="65c42-107">Os estilos de parágrafo são definidos por meio do elemento de `w:pPr` ; se um parágrafo não contém esse elemento, é formatado com o estilo padrão.</span><span class="sxs-lookup"><span data-stu-id="65c42-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="65c42-108">Este tópico explica o significado de algumas partes de consulta, então mostra a consulta como parte de um exemplo completo, que funciona.</span><span class="sxs-lookup"><span data-stu-id="65c42-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65c42-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65c42-109">Example</span></span>  
 <span data-ttu-id="65c42-110">A fonte da consulta para recuperar todos os parágrafos em um documento e seus estilos é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="65c42-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="65c42-111">Esta expressão é semelhante à fonte da consulta no exemplo anterior, [Localizando o estilo de parágrafo padrão (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="65c42-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="65c42-112">A principal diferença é que usa o eixo de <xref:System.Xml.Linq.XContainer.Descendants%2A> em vez do eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="65c42-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="65c42-113">A consulta usa o eixo de <xref:System.Xml.Linq.XContainer.Descendants%2A> porque em documentos que têm seções, os parágrafos não serão os filhos diretos do elemento do corpo; em vez, os parágrafos serão dois níveis para baixo na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="65c42-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="65c42-114">Usando o eixo de <xref:System.Xml.Linq.XContainer.Descendants%2A> , o código funcionará de mesmo se o documento usa seções.</span><span class="sxs-lookup"><span data-stu-id="65c42-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65c42-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65c42-115">Example</span></span>  
 <span data-ttu-id="65c42-116">A consulta usa uma cláusula de `let` para determinar o elemento que contém o nó de estilo.</span><span class="sxs-lookup"><span data-stu-id="65c42-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="65c42-117">Se não houver nenhum elemento, então `styleNode` é definido como `null`:</span><span class="sxs-lookup"><span data-stu-id="65c42-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="65c42-118">A cláusula de `let` primeiro usa o eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> para localizar todos os elementos chamados `pPr`, então usa o método de extensão de <xref:System.Xml.Linq.Extensions.Elements%2A> para localizar todos os elementos filho chamados `pStyle`, e finalmente usa o operador padrão de consulta de <xref:System.Linq.Enumerable.FirstOrDefault%2A> para converter a um único.</span><span class="sxs-lookup"><span data-stu-id="65c42-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="65c42-119">Se a coleção estiver vazia, `styleNode` é definido como `null`.</span><span class="sxs-lookup"><span data-stu-id="65c42-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="65c42-120">Este é um idioma útil para procurar o nó descendente de `pStyle` .</span><span class="sxs-lookup"><span data-stu-id="65c42-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="65c42-121">Observe que se o nó filho de `pPr` não existir, o código faz ou falhas lançando uma exceção; em vez disso, `styleNode` é definido como `null`, que é o comportamento desejado desta cláusula de `let` .</span><span class="sxs-lookup"><span data-stu-id="65c42-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="65c42-122">A consulta em uma coleção de um tipo anônimo com dois membros, `StyleName` e `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="65c42-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65c42-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65c42-123">Example</span></span>  
 <span data-ttu-id="65c42-124">Este exemplo processa um documento de WordprocessingML, recuperando os nós de parágrafo de um documento de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="65c42-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="65c42-125">Também identifica o estilo de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="65c42-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="65c42-126">Este exemplo cria nos exemplos anteriores neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="65c42-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="65c42-127">A nova consulta é chamada nos comentários no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="65c42-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="65c42-128">É possível obter instruções para criar o documento de origem deste exemplo em [Criando o documento do Office Open XML de origem (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="65c42-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="65c42-129">Este exemplo usa as classes encontradas no assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="65c42-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="65c42-130">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65c42-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="65c42-131">Este exemplo produz a seguinte saída quando aplicado ao documento descrito em [Criando o documento do Office Open XML de origem (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="65c42-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
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
  
## <a name="next-steps"></a><span data-ttu-id="65c42-132">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="65c42-132">Next Steps</span></span>  
 <span data-ttu-id="65c42-133">No próximo tópico, [Recuperando o texto dos parágrafos (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), você criará uma consulta para recuperar o texto dos parágrafos.</span><span class="sxs-lookup"><span data-stu-id="65c42-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c42-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65c42-134">See also</span></span>

- [<span data-ttu-id="65c42-135">Tutorial: manipulando conteúdo em um documento WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="65c42-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
