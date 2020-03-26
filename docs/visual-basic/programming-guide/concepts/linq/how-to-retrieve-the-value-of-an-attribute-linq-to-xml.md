---
title: Como recuperar o valor de um atributo (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 6593639dcdc234ddda808cfdb5e85ebe1a771b62
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248941"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="9e187-102">Como: Recuperar o Valor de um Atributo (LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e187-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="9e187-103">Este tópico mostra como obter o valor de atributos.</span><span class="sxs-lookup"><span data-stu-id="9e187-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="9e187-104">Existem duas maneiras principais: converter <xref:System.Xml.Linq.XAttribute> no tipo desejado; o operador de conversão explícita converte o conteúdo do elemento ou do atributo no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="9e187-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="9e187-105">Outra opção é usar a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="9e187-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="9e187-106">No entanto, a conversão geralmente é a abordagem recomendada.</span><span class="sxs-lookup"><span data-stu-id="9e187-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="9e187-107">Se você lançar o atributo para um tipo de valor anulado, o código é mais simples de escrever ao recuperar o valor de um atributo que pode ou não existir.</span><span class="sxs-lookup"><span data-stu-id="9e187-107">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="9e187-108">Para exemplos desta técnica, consulte [Como: Recuperar o Valor de um Elemento (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9e187-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e187-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e187-109">Example</span></span>  
 <span data-ttu-id="9e187-110">Em Visual Basic, você pode usar a propriedade de atributo integrado para recuperar o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="9e187-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="9e187-111">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="9e187-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="9e187-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e187-112">Example</span></span>  
 <span data-ttu-id="9e187-113">Em Visual Basic, você pode usar a propriedade de atributo integrado para definir o valor de um atributo.</span><span class="sxs-lookup"><span data-stu-id="9e187-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="9e187-114">Além disso, se você usar a propriedade de atributo integrado para definir o valor de um atributo que não existe, o atributo será criado.</span><span class="sxs-lookup"><span data-stu-id="9e187-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="9e187-115">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="9e187-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="9e187-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e187-116">Example</span></span>  
 <span data-ttu-id="9e187-117">O exemplo a seguir mostra como recuperar o valor de um atributo em que o atributo está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="9e187-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="9e187-118">Para obter mais informações, consulte [Visão Geral de Namespaces (LINQ para XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9e187-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9e187-119">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="9e187-119">This example produces the following output:</span></span>  
  
```console  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e187-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="9e187-120">See also</span></span>

- [<span data-ttu-id="9e187-121">Eixos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e187-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
