---
title: 'Como: Trabalhar com dicionários usando LINQ to XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: 9f08430aeb92b9c6e0b7b08481027fb3b5b77cad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572338"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a><span data-ttu-id="e12e0-102">Como: Trabalhar com dicionários usando LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e12e0-102">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="e12e0-103">É conveniente converter variedades de estruturas de dados para XML, e XML de volta para outras estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="e12e0-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="e12e0-104">Este tópico mostra uma implementação específica dessa abordagem geral convertendo <xref:System.Collections.Generic.Dictionary%602> a XML e verso.</span><span class="sxs-lookup"><span data-stu-id="e12e0-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e12e0-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e12e0-105">Example</span></span>  
 <span data-ttu-id="e12e0-106">Este exemplo usa literais XML e uma consulta em uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="e12e0-106">This example uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="e12e0-107">A consulta projetos novos <xref:System.Xml.Linq.XElement> objetos, que então se tornar o novo conteúdo para o `Root` <xref:System.Xml.Linq.XElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="e12e0-107">The query projects new <xref:System.Xml.Linq.XElement> objects, which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="e12e0-108">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e12e0-108">This code produces the following output:</span></span>  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e12e0-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e12e0-109">Example</span></span>  
 <span data-ttu-id="e12e0-110">O código a seguir cria um dicionário XML.</span><span class="sxs-lookup"><span data-stu-id="e12e0-110">The following code creates a dictionary from XML.</span></span>  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 <span data-ttu-id="e12e0-111">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e12e0-111">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="e12e0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e12e0-112">See also</span></span>
- [<span data-ttu-id="e12e0-113">Projeções e transformações (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e12e0-113">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
