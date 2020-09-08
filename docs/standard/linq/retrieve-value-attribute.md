---
title: Como recuperar o valor de um atributo-LINQ to XML
description: Recupere o valor de um atributo. Você pode converter um XAttribute para o tipo desejado ou usar a Propriedade XAttribute. Value.
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 7af3616c9808cad5dfb52f53c74b21a59da5c954
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552057"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml"></a><span data-ttu-id="81e1b-104">Como recuperar o valor de um atributo (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="81e1b-104">How to retrieve the value of an attribute (LINQ to XML)</span></span>

<span data-ttu-id="81e1b-105">Este artigo mostra como obter o valor de atributos.</span><span class="sxs-lookup"><span data-stu-id="81e1b-105">This article shows how to obtain the value of attributes.</span></span> <span data-ttu-id="81e1b-106">Existem duas maneiras principais: converter <xref:System.Xml.Linq.XAttribute> no tipo desejado; o operador de conversão explícita converte o conteúdo do elemento ou do atributo no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="81e1b-106">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="81e1b-107">Outra opção é usar a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="81e1b-107">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="81e1b-108">No entanto, a conversão geralmente é a abordagem recomendada.</span><span class="sxs-lookup"><span data-stu-id="81e1b-108">However, casting is generally the better approach.</span></span> <span data-ttu-id="81e1b-109">Se você converter o atributo para um tipo de valor anulável, o código será mais simples de escrever ao recuperar o valor de um atributo que pode ou não existir.</span><span class="sxs-lookup"><span data-stu-id="81e1b-109">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="81e1b-110">Para obter exemplos dessa técnica, consulte [como recuperar o valor de um elemento](retrieve-value-element.md).</span><span class="sxs-lookup"><span data-stu-id="81e1b-110">For examples of this technique, see [How to retrieve the value of an element](retrieve-value-element.md).</span></span>

## <a name="example-use-a-cast-to-retrieve-the-value-of-an-attribute"></a><span data-ttu-id="81e1b-111">Exemplo: usar uma conversão para recuperar o valor de um atributo</span><span class="sxs-lookup"><span data-stu-id="81e1b-111">Example: Use a cast to retrieve the value of an attribute</span></span>

<span data-ttu-id="81e1b-112">Para recuperar o valor de um atributo em C#, você converte o <xref:System.Xml.Linq.XAttribute> objeto para o tipo desejado.</span><span class="sxs-lookup"><span data-stu-id="81e1b-112">To retrieve the value of an attribute in C#, you cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span> <span data-ttu-id="81e1b-113">No Visual Basic, você pode usar a propriedade de atributo integrado para recuperar o valor.</span><span class="sxs-lookup"><span data-stu-id="81e1b-113">In Visual Basic, you can use the integrated attribute property to retrieve the value.</span></span>

```csharp
XElement root = new XElement("Root",
                    new XAttribute("Attr", "abcde")
                );
Console.WriteLine(root);
string str = (string)root.Attribute("Attr");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root Attr="abcde"/>
Console.WriteLine(root)
Dim str As String = root.@Attr
Console.WriteLine(str)
```

<span data-ttu-id="81e1b-114">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="81e1b-114">This example produces the following output:</span></span>

```output
<Root Attr="abcde" />
abcde
```

## <a name="example-use-a-cast-to-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="81e1b-115">Exemplo: usar uma conversão para recuperar do XML que está em um namespace</span><span class="sxs-lookup"><span data-stu-id="81e1b-115">Example: Use a cast to retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="81e1b-116">O exemplo a seguir mostra como recuperar o valor de um atributo se o atributo estiver em um namespace.</span><span class="sxs-lookup"><span data-stu-id="81e1b-116">The following example shows how to retrieve the value of an attribute if the attribute is in a namespace.</span></span> <span data-ttu-id="81e1b-117">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="81e1b-117">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
                    new XAttribute(aw + "Attr", "abcde")
                );
string str = (string)root.Attribute(aw + "Attr");
Console.WriteLine(str);
```

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

<span data-ttu-id="81e1b-118">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="81e1b-118">This example produces the following output:</span></span>

```output
abcde
```

## <a name="see-also"></a><span data-ttu-id="81e1b-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="81e1b-119">See also</span></span>

- [<span data-ttu-id="81e1b-120">Visão geral dos eixos de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="81e1b-120">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
