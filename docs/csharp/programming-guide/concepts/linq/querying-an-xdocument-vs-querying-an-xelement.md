---
title: Consultando um XDocument vs. consultando um XElement (C#)
description: Saiba mais sobre as diferenças entre consultar um XDocument e consultar um XElement. Examine os exemplos de código que demonstram essas diferenças.
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 0c81768f06148308a639f96f4041e464b24edd33
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300300"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="f5e17-104">Consultando um XDocument vs. consultando um XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="f5e17-104">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="f5e17-105">Ao carregar um documento por meio do <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, você observará que precisa escrever consultas um pouco diferentes do que ao carregar por meio do <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5e17-105">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="f5e17-106">Comparação de XDocument.Load e de XElement.Load</span><span class="sxs-lookup"><span data-stu-id="f5e17-106">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="f5e17-107">Quando você carrega um documento XML em um <xref:System.Xml.Linq.XElement> por meio do <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, o <xref:System.Xml.Linq.XElement> na raiz da árvore XML contém o elemento raiz do documento carregado.</span><span class="sxs-lookup"><span data-stu-id="f5e17-107">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="f5e17-108">No entanto, quando você carrega o mesmo documento XML em um <xref:System.Xml.Linq.XDocument> por meio do <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, a raiz da árvore é um nó de <xref:System.Xml.Linq.XDocument>, e o elemento raiz do documento carregado é o nó filho <xref:System.Xml.Linq.XElement> permitido do <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="f5e17-108">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="f5e17-109">Os eixos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] operam em relação ao nó raiz.</span><span class="sxs-lookup"><span data-stu-id="f5e17-109">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="f5e17-110">Este primeiro exemplo carrega uma árvore XML usando <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="f5e17-110">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="f5e17-111">Em seguida, ele consulta os elementos filho da raiz da árvore.</span><span class="sxs-lookup"><span data-stu-id="f5e17-111">It then queries for the child elements of the root of the tree.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="f5e17-112">Como esperado, Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="f5e17-112">As expected, this example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="f5e17-113">O exemplo a seguir é o mesmo que o anterior, com a exceção de que a árvore XML é carregada em um <xref:System.Xml.Linq.XDocument> em vez de em um <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f5e17-113">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="f5e17-114">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="f5e17-114">This example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="f5e17-115">Observe que a mesma consulta retornou o nó `Root` em vez dos três nós filho.</span><span class="sxs-lookup"><span data-stu-id="f5e17-115">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="f5e17-116">Uma abordagem para lidar com isso é usar a propriedade <xref:System.Xml.Linq.XDocument.Root%2A> antes de acessar os métodos de eixos, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f5e17-116">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="f5e17-117">Essa consulta agora executa da mesma maneira que a consulta na árvore enraizada em <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f5e17-117">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="f5e17-118">O exemplo produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="f5e17-118">The example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  