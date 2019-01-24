---
title: Consultar um XDocument versus Consultar um XElement (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 8d13276b6d66d0ec3768182df7b4324678174fae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579833"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a><span data-ttu-id="27312-102">Consultar um XDocument versus Consultar um XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27312-102">Querying an XDocument vs. Querying an XElement (Visual Basic)</span></span>
<span data-ttu-id="27312-103">Ao carregar um documento por meio do <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, você observará que precisa escrever consultas um pouco diferentes do que ao carregar por meio do <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="27312-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="27312-104">Comparação de XDocument.Load e de XElement.Load</span><span class="sxs-lookup"><span data-stu-id="27312-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="27312-105">Quando você carrega um documento XML em um <xref:System.Xml.Linq.XElement> por meio do <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, o <xref:System.Xml.Linq.XElement> na raiz da árvore XML contém o elemento raiz do documento carregado.</span><span class="sxs-lookup"><span data-stu-id="27312-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="27312-106">No entanto, quando você carrega o mesmo documento XML em um <xref:System.Xml.Linq.XDocument> por meio do <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, a raiz da árvore é um nó de <xref:System.Xml.Linq.XDocument>, e o elemento raiz do documento carregado é o nó filho <xref:System.Xml.Linq.XElement> permitido do <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="27312-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="27312-107">Os eixos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] operam em relação ao nó raiz.</span><span class="sxs-lookup"><span data-stu-id="27312-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="27312-108">Este primeiro exemplo carrega uma árvore XML usando <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="27312-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="27312-109">Em seguida, ele consulta os elementos filho da raiz da árvore.</span><span class="sxs-lookup"><span data-stu-id="27312-109">It then queries for the child elements of the root of the tree.</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="27312-110">Como esperado, Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="27312-110">As expected, this example produces the following output:</span></span>  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="27312-111">O exemplo a seguir é o mesmo que o anterior, com a exceção de que a árvore XML é carregada em um <xref:System.Xml.Linq.XDocument> em vez de em um <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="27312-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="27312-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="27312-112">This example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="27312-113">Observe que a mesma consulta retornou o nó `Root` em vez dos três nós filho.</span><span class="sxs-lookup"><span data-stu-id="27312-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="27312-114">Uma abordagem para lidar com isso é usar a propriedade <xref:System.Xml.Linq.XDocument.Root%2A> antes de acessar os métodos de eixos, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="27312-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="27312-115">Essa consulta agora executa da mesma maneira que a consulta na árvore enraizada em <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="27312-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="27312-116">O exemplo produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="27312-116">The example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27312-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27312-117">See also</span></span>
- [<span data-ttu-id="27312-118">Consultas básicas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27312-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
