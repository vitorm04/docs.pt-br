---
title: 'Como: recuperar um único atributo (LINQ para XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: e9e4dce95e9c3202b1cd2a53c186126deac0913c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642944"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="e01dc-102">Como: recuperar um único atributo (LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e01dc-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="e01dc-103">Este tópico explica como recuperar um único atributo de um elemento, dado o nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="e01dc-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="e01dc-104">Isso é útil para gravar as expressões de consulta onde você deseja localizar um elemento que possui um atributo específico.</span><span class="sxs-lookup"><span data-stu-id="e01dc-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="e01dc-105">O método de <xref:System.Xml.Linq.XElement.Attribute%2A> da classe de <xref:System.Xml.Linq.XElement> retorna <xref:System.Xml.Linq.XAttribute> com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="e01dc-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e01dc-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e01dc-106">Example</span></span>  
 <span data-ttu-id="e01dc-107">O exemplo a seguir usa o método <xref:System.Xml.Linq.XElement.Attribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="e01dc-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 <span data-ttu-id="e01dc-108">Este exemplo localiza os descendentes na árvore chamada `Phone`, e localiza o atributo chamado `type`.</span><span class="sxs-lookup"><span data-stu-id="e01dc-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="e01dc-109">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e01dc-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="e01dc-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e01dc-110">Example</span></span>  
 <span data-ttu-id="e01dc-111">Se você deseja recuperar o valor do atributo, você pode convertê-lo, exatamente como você faz para com objetos de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="e01dc-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="e01dc-112">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="e01dc-112">The following example demonstrates this.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 <span data-ttu-id="e01dc-113">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e01dc-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="e01dc-114"> fornece operadores cast explícitos para a classe <xref:System.Xml.Linq.XAttribute> para `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` e `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="e01dc-114"> provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e01dc-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e01dc-115">Example</span></span>  
 <span data-ttu-id="e01dc-116">O exemplo a seguir mostra o mesmo código para um atributo que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="e01dc-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="e01dc-117">Para obter mais informações, consulte [trabalhando com Namespaces de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="e01dc-117">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e01dc-118">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e01dc-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="e01dc-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e01dc-119">See Also</span></span>  
 [<span data-ttu-id="e01dc-120">Eixos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e01dc-120">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
