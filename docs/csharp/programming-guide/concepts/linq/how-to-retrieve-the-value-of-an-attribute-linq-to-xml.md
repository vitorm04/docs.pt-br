---
title: Como recuperar o valor de um atributo (LINQ para XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 212ad3bb3097e7e2c76da8f165011b181f329d4c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249188"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="a0209-102">Como recuperar o valor de um atributo (LINQ para XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0209-102">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="a0209-103">Este tópico mostra como obter o valor de atributos.</span><span class="sxs-lookup"><span data-stu-id="a0209-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="a0209-104">Existem duas maneiras principais: converter <xref:System.Xml.Linq.XAttribute> no tipo desejado; o operador de conversão explícita converte o conteúdo do elemento ou do atributo no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="a0209-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="a0209-105">Outra opção é usar a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0209-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="a0209-106">No entanto, a conversão geralmente é a abordagem recomendada.</span><span class="sxs-lookup"><span data-stu-id="a0209-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="a0209-107">Se você lançar o atributo para um tipo de valor anulado, o código é mais simples de escrever ao recuperar o valor de um atributo que pode ou não existir.</span><span class="sxs-lookup"><span data-stu-id="a0209-107">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="a0209-108">Para exemplos desta técnica, consulte [Como recuperar o valor de um elemento (LINQ para XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a0209-108">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0209-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0209-109">Example</span></span>  
 <span data-ttu-id="a0209-110">Para recuperar o valor de um atributo, basta converter o objeto <xref:System.Xml.Linq.XAttribute> no tipo desejado.</span><span class="sxs-lookup"><span data-stu-id="a0209-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="a0209-111">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a0209-111">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="a0209-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0209-112">Example</span></span>  
 <span data-ttu-id="a0209-113">O exemplo a seguir mostra como recuperar o valor de um atributo em que o atributo está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="a0209-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="a0209-114">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a0209-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="a0209-115">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a0209-115">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0209-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="a0209-116">See also</span></span>

- [<span data-ttu-id="a0209-117">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a0209-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
