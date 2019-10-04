---
title: 'Como: Analisar uma cadeia de caracteres (C#)'
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 16310e37afec950c372c7b47637986bb0eb399b8
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956618"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="61d05-102">Como: Analisar uma cadeia de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="61d05-102">How to: Parse a String (C#)</span></span>

<span data-ttu-id="61d05-103">Este tópico mostra como analisar uma cadeia de caracteres para criar uma árvore XML no C#.</span><span class="sxs-lookup"><span data-stu-id="61d05-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="61d05-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61d05-104">Example</span></span>

<span data-ttu-id="61d05-105">O código C# a seguir mostra como analisar uma cadeia de caracteres XML:</span><span class="sxs-lookup"><span data-stu-id="61d05-105">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="61d05-106">O nó `Contacts` raiz tem dois nós `Contact`.</span><span class="sxs-lookup"><span data-stu-id="61d05-106">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="61d05-107">Para acessar alguns dados específicos em seu XML analisado, use o método [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) , que, nesse caso, retorna os elementos filho do nó `Contacts` raiz.</span><span class="sxs-lookup"><span data-stu-id="61d05-107">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="61d05-108">O exemplo a seguir imprime o primeiro nó `Contact` no console:</span><span class="sxs-lookup"><span data-stu-id="61d05-108">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a><span data-ttu-id="61d05-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61d05-109">See also</span></span>

- [<span data-ttu-id="61d05-110">Como: Localizar um elemento com um atributo específico (C#)</span><span class="sxs-lookup"><span data-stu-id="61d05-110">How to: Find an Element with a Specific Attribute (C#)</span></span>](how-to-find-an-element-with-a-specific-attribute.md)
