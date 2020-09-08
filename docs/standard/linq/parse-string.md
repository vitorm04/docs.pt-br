---
title: Como analisar um LINQ to XML de cadeia de caracteres
description: Você pode analisar uma cadeia de caracteres com XElement. Parse para criar uma árvore XML em C# e Visual Basic e pode criar uma árvore XML com literais XML no Visual Basic.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: f4bd22acbf3b11d801c791cc591d882810450fd4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551904"
---
# <a name="how-to-parse-a-string-linq-to-xml"></a><span data-ttu-id="f33c4-103">Como analisar uma cadeia de caracteres (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f33c4-103">How to parse a string (LINQ to XML)</span></span>

<span data-ttu-id="f33c4-104">Este artigo mostra como analisar uma cadeia de caracteres para criar uma árvore XML em C# e em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f33c4-104">This article shows how to parse a string to create an XML tree in C# and in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="f33c4-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f33c4-105">Example</span></span>

<span data-ttu-id="f33c4-106">O código C# a seguir mostra como analisar uma cadeia de caracteres XML:</span><span class="sxs-lookup"><span data-stu-id="f33c4-106">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="f33c4-107">Você pode analisar uma cadeia de caracteres em Visual Basic de maneira semelhante.</span><span class="sxs-lookup"><span data-stu-id="f33c4-107">You can parse a string in Visual Basic in a similar manner.</span></span> <span data-ttu-id="f33c4-108">No entanto, é mais eficiente usar literais XML, como mostrado no código a seguir, porque os literais XML não sofrem com as mesmas penalidades de desempenho que a análise de XML de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f33c4-108">However, it's more efficient to use XML literals, as shown in following code, because XML literals don't suffer from the same performance penalties as parsing XML from a string.</span></span>

<span data-ttu-id="f33c4-109">Usando literais XML, você pode simplesmente copiar e colar o XML em seu programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f33c4-109">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>

> [!NOTE]
> <span data-ttu-id="f33c4-110">Analisar texto ou carregar um documento XML de um arquivo de texto é menos eficiente do que a construção funcional.</span><span class="sxs-lookup"><span data-stu-id="f33c4-110">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="f33c4-111">Se você estiver inicializando uma árvore XML do código, levará menos tempo do processador para usar a construção funcional do que analisar o texto.</span><span class="sxs-lookup"><span data-stu-id="f33c4-111">If you're initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>

```vb
Dim contacts as XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type="home">206-555-0144</Phone>
            <Phone Type="work">425-555-0145</Phone>
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
            <Phone Type="mobile">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>
```

<span data-ttu-id="f33c4-112">O `Contacts` nó raiz tem dois `Contact` nós.</span><span class="sxs-lookup"><span data-stu-id="f33c4-112">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="f33c4-113">Para acessar alguns dados específicos em seu XML analisado, use o método [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) , que, nesse caso, retorna os elementos filho do `Contacts` nó raiz.</span><span class="sxs-lookup"><span data-stu-id="f33c4-113">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="f33c4-114">O exemplo a seguir imprime o primeiro `Contact` nó no console:</span><span class="sxs-lookup"><span data-stu-id="f33c4-114">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

```vb
Dim contactNodes As List(Of XElement) = contacts.Elements("Contact").ToList()
Console.WriteLine(contactNodes(0))
```

## <a name="see-also"></a><span data-ttu-id="f33c4-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="f33c4-115">See also</span></span>

- [<span data-ttu-id="f33c4-116">Como localizar um elemento com um atributo específico</span><span class="sxs-lookup"><span data-stu-id="f33c4-116">How to find an element with a specific attribute</span></span>](find-element-specific-attribute.md)
