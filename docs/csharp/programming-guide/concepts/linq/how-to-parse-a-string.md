---
title: Como analisar uma cadeia de caracteres (C#)
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 086a4baecee9ee927b08d6da53d16324ef32e8a8
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140982"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="24a45-102">Como analisar uma cadeia de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="24a45-102">How to: Parse a String (C#)</span></span>

<span data-ttu-id="24a45-103">Este tópico mostra como analisar uma cadeia de caracteres para criar uma árvore XML no C#.</span><span class="sxs-lookup"><span data-stu-id="24a45-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="24a45-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24a45-104">Example</span></span>

<span data-ttu-id="24a45-105">O código C# a seguir mostra como analisar uma cadeia de caracteres XML:</span><span class="sxs-lookup"><span data-stu-id="24a45-105">The following C# code shows how to parse an XML string:</span></span>

```csharp
XElement contacts = XElement.Parse(
    @"<Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type=""home"">206-555-0144</Phone>
            <Phone Type=""work"">425-555-0145</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>10</NetWorth>
        </Contact>
        <Contact>
            <Name>Gretchen Rivas</Name>
            <Phone Type=""mobile"">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>");
Console.WriteLine(contacts);
```

<span data-ttu-id="24a45-106">O nó de `Contacts` raiz tem dois nós `Contact`.</span><span class="sxs-lookup"><span data-stu-id="24a45-106">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="24a45-107">Para acessar alguns dados específicos em seu XML analisado, use o método [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) , que, nesse caso, retorna os elementos filho do nó de `Contacts` raiz.</span><span class="sxs-lookup"><span data-stu-id="24a45-107">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="24a45-108">O exemplo a seguir imprime o primeiro nó `Contact` no console:</span><span class="sxs-lookup"><span data-stu-id="24a45-108">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a><span data-ttu-id="24a45-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24a45-109">See also</span></span>

- [<span data-ttu-id="24a45-110">Como localizar um elemento com um atributo específico (C#)</span><span class="sxs-lookup"><span data-stu-id="24a45-110">How to find an element with a specific attribute (C#)</span></span>](how-to-find-an-element-with-a-specific-attribute.md)
