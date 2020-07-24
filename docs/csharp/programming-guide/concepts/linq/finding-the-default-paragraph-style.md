---
title: Localizando o estilo de parágrafo padrão (C#)
description: Saiba como processar um documento do WordprocessingML com LINQ em C#. Este exemplo localiza o estilo padrão de parágrafos no documento.
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: e18bbbdbd5b2627c9ff4c3c3eedd84d7cb166a62
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103826"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="8f685-104">Localizando o estilo de parágrafo padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="8f685-104">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="8f685-105">A primeira tarefa no tutorial Manipulando informações em um documento de WordprocessingML é localizar o estilo padrão dos parágrafos no documento.</span><span class="sxs-lookup"><span data-stu-id="8f685-105">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f685-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f685-106">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8f685-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f685-107">Description</span></span>  
 <span data-ttu-id="8f685-108">O exemplo a seguir abre um documento do Office Open XML WordprocessingML, encontrar as partes do documento e estilo de pacote em seguida, executa uma consulta que localize o nome padrão de estilo.</span><span class="sxs-lookup"><span data-stu-id="8f685-108">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="8f685-109">Para obter informações sobre pacotes de documento do Office Open XML, bem como as partes que os compõem, consulte em [Detalhes de documentos do Office Open XML WordprocessingML (C#)](./wordprocessingml-document-with-styles.md).</span><span class="sxs-lookup"><span data-stu-id="8f685-109">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="8f685-110">A consulta encontrar um nó chamado `w:style` que tem um atributo chamado `w:type` com um valor de “parágrafo”, e também tem um atributo chamado `w:default` com um valor de “1 ".</span><span class="sxs-lookup"><span data-stu-id="8f685-110">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="8f685-111">Haverá porque apenas um nó XML com esses atributos, a consulta usa o operador de <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> para converter uma coleção para um único.</span><span class="sxs-lookup"><span data-stu-id="8f685-111">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="8f685-112">Então obtém o valor do atributo com o nome `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="8f685-112">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="8f685-113">Este exemplo usa classes do assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="8f685-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="8f685-114">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f685-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8f685-115">Código</span><span class="sxs-lookup"><span data-stu-id="8f685-115">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="8f685-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f685-116">Comments</span></span>  
 <span data-ttu-id="8f685-117">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="8f685-117">This example produces the following output:</span></span>  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="8f685-118">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8f685-118">Next Steps</span></span>  
 <span data-ttu-id="8f685-119">No exemplo a seguir, você criará uma consulta semelhante que localiza todos os parágrafos em um documento e seus estilos:</span><span class="sxs-lookup"><span data-stu-id="8f685-119">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="8f685-120">Recuperando os parágrafos e seus estilos (C#)</span><span class="sxs-lookup"><span data-stu-id="8f685-120">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  
