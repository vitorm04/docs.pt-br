---
title: 'Como: Recuperar o valor de um atributo (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 7cdd3e1f3e4c15d99511e944fd9bc2faac17dc5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054452"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="676b7-102">Como: Recuperar o valor de um atributo (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="676b7-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="676b7-103">Este tópico mostra como obter o valor de atributos.</span><span class="sxs-lookup"><span data-stu-id="676b7-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="676b7-104">Há duas maneiras principais: Você pode converter um <xref:System.Xml.Linq.XAttribute> no tipo desejado; o operador de conversão explícita converte então o conteúdo do elemento ou do atributo no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="676b7-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="676b7-105">Outra opção é usar a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="676b7-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="676b7-106">No entanto, a conversão geralmente é a abordagem recomendada.</span><span class="sxs-lookup"><span data-stu-id="676b7-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="676b7-107">Se você converter o atributo em um tipo anulável, o código será mais simples de criar ao recuperar o valor de um atributo que pode ou não existir.</span><span class="sxs-lookup"><span data-stu-id="676b7-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="676b7-108">Para obter exemplos dessa técnica, confira [Como: Recuperar o valor de um elemento (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="676b7-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="676b7-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="676b7-109">Example</span></span>  
 <span data-ttu-id="676b7-110">Em Visual Basic, você pode usar a propriedade de atributo integrado para recuperar o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="676b7-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="676b7-111">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="676b7-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="676b7-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="676b7-112">Example</span></span>  
 <span data-ttu-id="676b7-113">Em Visual Basic, você pode usar a propriedade de atributo integrado para definir o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="676b7-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="676b7-114">Além disso, se você usar a propriedade de atributo integrado para definir o valor de um atributo que não existe, o atributo será criado.</span><span class="sxs-lookup"><span data-stu-id="676b7-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="676b7-115">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="676b7-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="676b7-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="676b7-116">Example</span></span>  
 <span data-ttu-id="676b7-117">O exemplo a seguir mostra como recuperar o valor de um atributo em que o atributo está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="676b7-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="676b7-118">Para obter mais informações, consulte [trabalhando com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="676b7-118">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="676b7-119">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="676b7-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="676b7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="676b7-120">See also</span></span>

- [<span data-ttu-id="676b7-121">Eixos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="676b7-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
