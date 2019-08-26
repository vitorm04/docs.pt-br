---
title: Refatoração usando um método de extensão (C#)
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: 2be848d6454abf0dd37a6974cff915a107336503
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591304"
---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="09b21-102">Refatoração usando um método de extensão (C#)</span><span class="sxs-lookup"><span data-stu-id="09b21-102">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="09b21-103">Este exemplo se baseia no exemplo anterior, [Recuperando o texto dos parágrafos (C#)](./retrieving-the-text-of-the-paragraphs.md), refatorando a concatenação de cadeias de caracteres usando uma função pura implementada como um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="09b21-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="09b21-104">O exemplo anterior usa o operador padrão de consulta de <xref:System.Linq.Enumerable.Aggregate%2A> para concatenar várias cadeias de caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="09b21-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="09b21-105">No entanto, é mais conveniente escrever um método de extensão para fazer isso, porque a consulta resultante menor e mais simples.</span><span class="sxs-lookup"><span data-stu-id="09b21-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09b21-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09b21-106">Example</span></span>  
 <span data-ttu-id="09b21-107">Este exemplo processa um documento de WordprocessingML, recuperando os parágrafos, o estilo de cada parágrafo, e o texto de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="09b21-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="09b21-108">Este exemplo cria nos exemplos anteriores neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="09b21-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="09b21-109">O exemplo contém várias sobrecargas de método `StringConcatenate` .</span><span class="sxs-lookup"><span data-stu-id="09b21-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="09b21-110">É possível obter instruções para criar o documento de origem deste exemplo em [Criando o documento do Office Open XML de origem (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="09b21-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="09b21-111">Este exemplo usa classes do assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="09b21-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="09b21-112">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09b21-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="09b21-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09b21-113">Example</span></span>  
 <span data-ttu-id="09b21-114">Há quatro sobrecargas de método `StringConcatenate` .</span><span class="sxs-lookup"><span data-stu-id="09b21-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="09b21-115">Uma sobrecarga toma apenas uma coleção de cadeias de caracteres e retorna uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="09b21-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="09b21-116">Outra sobrecarga pode ter uma coleção de qualquer tipo, e um delegado esse projetos de um singleton da coleção como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="09b21-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="09b21-117">Existem mais duas sobrecargas que permitem que você especifique uma cadeia de caracteres separator.</span><span class="sxs-lookup"><span data-stu-id="09b21-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="09b21-118">O código a seguir usa todas as quatro sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="09b21-118">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="09b21-119">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="09b21-119">This example produces the following output:</span></span>  
  
```  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="09b21-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09b21-120">Example</span></span>  
 <span data-ttu-id="09b21-121">Agora, o exemplo pode ser alterado para aproveitar o novo método de extensão:</span><span class="sxs-lookup"><span data-stu-id="09b21-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
  
 <span data-ttu-id="09b21-122">Este exemplo produz a seguinte saída quando aplicado ao documento descrito em [Criando o documento do Office Open XML de origem (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="09b21-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
 <span data-ttu-id="09b21-123">Observe que essa que refatoração é uma variante de refatoração em uma função pura.</span><span class="sxs-lookup"><span data-stu-id="09b21-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="09b21-124">O próximo tópico introduzir a exibição de incluir em funções puras com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="09b21-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="09b21-125">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="09b21-125">Next Steps</span></span>  
 <span data-ttu-id="09b21-126">O exemplo a seguir mostra como refatorar esse código em outra maneira, usando funções puras:</span><span class="sxs-lookup"><span data-stu-id="09b21-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="09b21-127">Refatoração usando uma função pura (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09b21-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="09b21-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09b21-128">See also</span></span>

- [<span data-ttu-id="09b21-129">Tutorial: manipulando conteúdo em um documento WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="09b21-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="09b21-130">Refatoração em funções puras (C#)</span><span class="sxs-lookup"><span data-stu-id="09b21-130">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)
