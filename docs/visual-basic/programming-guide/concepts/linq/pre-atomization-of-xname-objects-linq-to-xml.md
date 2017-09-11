---
title: "A pré-compilação Atomização de XName objetos (LINQ to XML) (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4871fab18d04ce9d715299fd06138c493e666466
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="3fd93-102">A pré-compilação Atomização de XName objetos (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fd93-102">Pre-Atomization of XName Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3fd93-103">Uma maneira de melhorar o desempenho em LINQ to XML é pré-compilação atomizar <xref:System.Xml.Linq.XName>objetos.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="3fd93-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="3fd93-104">A pré-compilação atomização significa que você atribuir uma cadeia de caracteres para um <xref:System.Xml.Linq.XName>antes de criar a árvore XML usando os construtores de objeto de <xref:System.Xml.Linq.XElement>e <xref:System.Xml.Linq.XAttribute>classes.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="3fd93-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="3fd93-105">Em seguida, em vez de passar uma cadeia de caracteres para o construtor, que usaria a conversão implícita de cadeia de caracteres para <xref:System.Xml.Linq.XName>, você passa o inicializado <xref:System.Xml.Linq.XName>objeto.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="3fd93-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="3fd93-106">Isso melhora o desempenho quando você cria uma grande árvore XML em que os nomes específicos são repetidos.</span><span class="sxs-lookup"><span data-stu-id="3fd93-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="3fd93-107">Para fazer isso, você pode declarar e inicializar <xref:System.Xml.Linq.XName>objetos antes de construir a árvore XML e, em seguida, usar o <xref:System.Xml.Linq.XName>objetos em vez de especificar cadeias de caracteres para os nomes de elemento e atributo.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="3fd93-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="3fd93-108">Essa técnica pode produzir ganhos significativos de desempenho se você estiver criando um grande número de elementos ou atributos () com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="3fd93-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="3fd93-109">Você deve testar a pré-compilação atomização com seu cenário para decidir se você usar o.</span><span class="sxs-lookup"><span data-stu-id="3fd93-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fd93-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3fd93-110">Example</span></span>  
 <span data-ttu-id="3fd93-111">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="3fd93-111">The following example demonstrates this.</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="3fd93-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3fd93-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="3fd93-113">O exemplo a seguir mostra a mesma técnica onde o documento XML é em um namespace:</span><span class="sxs-lookup"><span data-stu-id="3fd93-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="3fd93-114">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3fd93-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="3fd93-115">O exemplo a seguir é mais semelhante ao que você provavelmente encontrará no mundo real.</span><span class="sxs-lookup"><span data-stu-id="3fd93-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="3fd93-116">Nesse exemplo, o conteúdo do elemento é fornecido por uma consulta:</span><span class="sxs-lookup"><span data-stu-id="3fd93-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 <span data-ttu-id="3fd93-117">O exemplo anterior executa melhor do que o exemplo, em que os nomes não são atomizados passos:</span><span class="sxs-lookup"><span data-stu-id="3fd93-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fd93-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fd93-118">See Also</span></span>  
 <span data-ttu-id="3fd93-119">[Desempenho (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="3fd93-119">[Performance (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md) </span></span>  
<span data-ttu-id="3fd93-120"> [Atomizados de XName e XNamespace objeto (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="3fd93-120"> [Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)</span></span>
