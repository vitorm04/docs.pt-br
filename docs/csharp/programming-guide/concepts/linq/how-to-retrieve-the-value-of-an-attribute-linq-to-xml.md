---
title: Como recuperar o valor de um atributo (LINQ to XML) (C#)
description: Saiba como obter o valor de um atributo. Consulte exemplos de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 5ee6995a54829b6d992e2982e6a6effcabf76470
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301548"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="0b598-104">Como recuperar o valor de um atributo (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0b598-104">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0b598-105">Este tópico mostra como obter o valor de atributos.</span><span class="sxs-lookup"><span data-stu-id="0b598-105">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="0b598-106">Existem duas maneiras principais: converter <xref:System.Xml.Linq.XAttribute> no tipo desejado; o operador de conversão explícita converte o conteúdo do elemento ou do atributo no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="0b598-106">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="0b598-107">Outra opção é usar a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b598-107">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="0b598-108">No entanto, a conversão geralmente é a abordagem recomendada.</span><span class="sxs-lookup"><span data-stu-id="0b598-108">However, casting is generally the better approach.</span></span> <span data-ttu-id="0b598-109">Se você converter o atributo para um tipo de valor anulável, o código será mais simples de escrever ao recuperar o valor de um atributo que pode ou não existir.</span><span class="sxs-lookup"><span data-stu-id="0b598-109">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="0b598-110">Para obter exemplos dessa técnica, consulte [como recuperar o valor de um elemento (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0b598-110">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b598-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b598-111">Example</span></span>  
 <span data-ttu-id="0b598-112">Para recuperar o valor de um atributo, basta converter o objeto <xref:System.Xml.Linq.XAttribute> no tipo desejado.</span><span class="sxs-lookup"><span data-stu-id="0b598-112">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="0b598-113">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="0b598-113">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="0b598-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b598-114">Example</span></span>  
 <span data-ttu-id="0b598-115">O exemplo a seguir mostra como recuperar o valor de um atributo em que o atributo está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="0b598-115">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="0b598-116">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0b598-116">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="0b598-117">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="0b598-117">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b598-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="0b598-118">See also</span></span>

- [<span data-ttu-id="0b598-119">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0b598-119">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
