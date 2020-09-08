---
title: Como detectar erros de análise-LINQ to XML
description: Uma exceção pode ocorrer em seu programa C# ou Visual Basic se tentar analisar um XML inválido com um método como XElement. Parse. Você pode escrever o programa para detectar e responder a essas exceções.
ms.date: 7/20/2015
dev_langs:
- csharp
- vb
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: f7679bd5a0726c669eb47ad6ad66e0f64259264b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551886"
---
# <a name="how-to-catch-parsing-errors-linq-to-xml"></a><span data-ttu-id="08a12-104">Como capturar erros de análise (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="08a12-104">How to catch parsing errors (LINQ to XML)</span></span>

<span data-ttu-id="08a12-105">Este artigo mostra como detectar XML mal formado ou inválido em C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="08a12-105">This article shows how to detect badly formed or invalid XML in C# or Visual Basic.</span></span>

<span data-ttu-id="08a12-106">O LINQ to XML é implementado usando <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="08a12-106">LINQ to XML is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="08a12-107">Se XML mal formado ou inválido for passado para LINQ to XML, a <xref:System.Xml.XmlReader> classe subjacente gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="08a12-107">If badly formed or invalid XML is passed to LINQ to XML, the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="08a12-108">Os vários métodos que analisam XML, como <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , não capturam a exceção; a exceção pode ser detectada pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08a12-108">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, don't catch the exception; the exception can then be caught by your application.</span></span>

## <a name="example-parse-invalid-xml"></a><span data-ttu-id="08a12-109">Exemplo: analisar XML inválido</span><span class="sxs-lookup"><span data-stu-id="08a12-109">Example: Parse invalid XML</span></span>

<span data-ttu-id="08a12-110">O código a seguir tenta analisar um XML inválido.</span><span class="sxs-lookup"><span data-stu-id="08a12-110">The following code tries to parse invalid XML.</span></span>

```csharp
try {
    XElement contacts = XElement.Parse(
        @"<Contacts>
            <Contact>
                <Name>Jim Wilson</Name>
            </Contact>
          </Contcts>");

    Console.WriteLine(contacts);
}
catch (System.Xml.XmlException e)
{
    Console.WriteLine(e.Message);
}
```

```vb
Try
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _
        "    <Contact>" & vbCrLf & _
        "        <Name>Jim Wilson</Name>" & vbCrLf & _
        "    </Contact>" & vbCrLf & _
        "</Contcts>")

    Console.WriteLine(contacts)
Catch e As System.Xml.XmlException
    Console.WriteLine(e.Message)
End Try
```

<span data-ttu-id="08a12-111">Devido à marca de fim inválida `</Contcts>` , o exemplo gera a seguinte exceção:</span><span class="sxs-lookup"><span data-stu-id="08a12-111">Because of the invalid end tag `</Contcts>`, the example throws the following exception:</span></span>

```output
The 'Contacts' start tag on line 1 doesn't match the end tag of 'Contcts'. Line 5, position 13.
```

<span data-ttu-id="08a12-112">Para obter informações sobre as exceções que <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> os <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> métodos,, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> e <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> geram, consulte a <xref:System.Xml.XmlReader> documentação.</span><span class="sxs-lookup"><span data-stu-id="08a12-112">For information about the exceptions that the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="08a12-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="08a12-113">See also</span></span>

- [<span data-ttu-id="08a12-114">Como analisar uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="08a12-114">How to parse a string</span></span>](parse-string.md)
