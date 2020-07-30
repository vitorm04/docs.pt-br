---
title: Refatoração usando um método de extensão (C#)
description: Saiba como refatorar o código usando um método de extensão. Consulte exemplos de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: e786f0e1514156535fd6a6033e37ed8879e99709
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381938"
---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="47c73-104">Refatoração usando um método de extensão (C#)</span><span class="sxs-lookup"><span data-stu-id="47c73-104">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="47c73-105">Este exemplo se baseia no exemplo anterior, [Recuperando o texto dos parágrafos (C#)](./retrieving-the-text-of-the-paragraphs.md), refatorando a concatenação de cadeias de caracteres usando uma função pura implementada como um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="47c73-105">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="47c73-106">O exemplo anterior usa o operador padrão de consulta de <xref:System.Linq.Enumerable.Aggregate%2A> para concatenar várias cadeias de caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="47c73-106">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="47c73-107">No entanto, é mais conveniente escrever um método de extensão para fazer isso, porque a consulta resultante menor e mais simples.</span><span class="sxs-lookup"><span data-stu-id="47c73-107">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47c73-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47c73-108">Example</span></span>  
 <span data-ttu-id="47c73-109">Este exemplo processa um documento de WordprocessingML, recuperando os parágrafos, o estilo de cada parágrafo, e o texto de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="47c73-109">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="47c73-110">Este exemplo cria nos exemplos anteriores neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="47c73-110">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="47c73-111">O exemplo contém várias sobrecargas de método `StringConcatenate` .</span><span class="sxs-lookup"><span data-stu-id="47c73-111">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="47c73-112">É possível obter instruções para criar o documento de origem deste exemplo em [Criando o documento do Office Open XML de origem (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="47c73-112">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="47c73-113">Este exemplo usa classes do assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="47c73-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="47c73-114">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47c73-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="47c73-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47c73-115">Example</span></span>  
 <span data-ttu-id="47c73-116">Há quatro sobrecargas de método `StringConcatenate` .</span><span class="sxs-lookup"><span data-stu-id="47c73-116">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="47c73-117">Uma sobrecarga toma apenas uma coleção de cadeias de caracteres e retorna uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="47c73-117">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="47c73-118">Outra sobrecarga pode ter uma coleção de qualquer tipo, e um delegado esse projetos de um singleton da coleção como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="47c73-118">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="47c73-119">Existem mais duas sobrecargas que permitem que você especifique uma cadeia de caracteres separator.</span><span class="sxs-lookup"><span data-stu-id="47c73-119">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="47c73-120">O código a seguir usa todas as quatro sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="47c73-120">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="47c73-121">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="47c73-121">This example produces the following output:</span></span>  
  
```output  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="47c73-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47c73-122">Example</span></span>  
 <span data-ttu-id="47c73-123">Agora, o exemplo pode ser alterado para aproveitar o novo método de extensão:</span><span class="sxs-lookup"><span data-stu-id="47c73-123">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
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
                    Uri styleUri =  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
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
  
        // Retrieve the text of each paragraph.  
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
                       .StringConcatenate(e => (string)e)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="47c73-124">Este exemplo produz a seguinte saída quando aplicado ao documento descrito em [Criando o documento do Office Open XML de origem (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="47c73-124">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
```output  
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
  
 <span data-ttu-id="47c73-125">Observe que essa que refatoração é uma variante de refatoração em uma função pura.</span><span class="sxs-lookup"><span data-stu-id="47c73-125">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="47c73-126">O próximo tópico introduzir a exibição de incluir em funções puras com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="47c73-126">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="47c73-127">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="47c73-127">Next Steps</span></span>  
 <span data-ttu-id="47c73-128">O exemplo a seguir mostra como refatorar esse código em outra maneira, usando funções puras:</span><span class="sxs-lookup"><span data-stu-id="47c73-128">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="47c73-129">Refatoração usando uma função pura (C#)</span><span class="sxs-lookup"><span data-stu-id="47c73-129">Refactoring Using a Pure Function (C#)</span></span>](./refactoring-using-a-pure-function.md)
  
## <a name="see-also"></a><span data-ttu-id="47c73-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="47c73-130">See also</span></span>

- [<span data-ttu-id="47c73-131">Tutorial: manipulando conteúdo em um documento WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="47c73-131">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="47c73-132">Refatoração em funções puras (C#)</span><span class="sxs-lookup"><span data-stu-id="47c73-132">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)
