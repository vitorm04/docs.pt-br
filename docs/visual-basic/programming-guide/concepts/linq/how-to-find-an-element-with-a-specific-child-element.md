---
title: 'Como: Localizar um elemento com um elemento filho específico (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: 1b226f009776f397f73ab9ee7826484eb8869f28
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827049"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a><span data-ttu-id="6414b-102">Como: Localizar um elemento com um elemento filho específico (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6414b-102">How to: Find an Element with a Specific Child Element (Visual Basic)</span></span>
<span data-ttu-id="6414b-103">Este tópico mostra como localizar determinado elemento que tem um elemento filho com um valor específico.</span><span class="sxs-lookup"><span data-stu-id="6414b-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6414b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6414b-104">Example</span></span>  
 <span data-ttu-id="6414b-105">O exemplo localiza o elemento `Test` que possui um elemento filho `CommandLine` com o valor "Examp2.EXE".</span><span class="sxs-lookup"><span data-stu-id="6414b-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="6414b-106">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Configuração de teste (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6414b-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 <span data-ttu-id="6414b-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="6414b-107">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
 <span data-ttu-id="6414b-108">Observe que este exemplo usa o [propriedade de eixo filho XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), o [propriedade de eixo de atributo XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)e o [propriedade XML Value](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="6414b-108">Note that this example uses the [XML Child axis property](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6414b-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6414b-109">Example</span></span>  
 <span data-ttu-id="6414b-110">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="6414b-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="6414b-111">Para obter mais informações, consulte [trabalhando com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="6414b-111">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="6414b-112">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Configuração de teste em um namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="6414b-112">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="6414b-113">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="6414b-113">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="6414b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6414b-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="6414b-115">Consultas básicas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6414b-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="6414b-116">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6414b-116">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="6414b-117">Operações de projeção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6414b-117">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
