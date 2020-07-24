---
title: Como capturar erros de análise (C#)
description: Este LINQ to XML exemplo em C# detecta XML incorretamente formado ou inválido. LINQ to XML usa XmlReader, que gera uma exceção para XML mal formado ou inválido.
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 0a891097322ef6acce062ea927692b01cc425e6c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105412"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="d2a23-104">Como capturar erros de análise (C#)</span><span class="sxs-lookup"><span data-stu-id="d2a23-104">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="d2a23-105">Este tópico mostra como detectar XML mal formado ou inválido.</span><span class="sxs-lookup"><span data-stu-id="d2a23-105">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d2a23-106">é implementado usando <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d2a23-106">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d2a23-107">Se malformado ou XML válido é passado para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], a classe subjacente de <xref:System.Xml.XmlReader> irá acionar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d2a23-107">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="d2a23-108">Os vários métodos que analisam XML, tais como <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, não capturam a exceção; a exceção pode ser capturada por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2a23-108">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2a23-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d2a23-109">Example</span></span>  
 <span data-ttu-id="d2a23-110">O código a seguir tenta analisar XML válido:</span><span class="sxs-lookup"><span data-stu-id="d2a23-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="d2a23-111">Quando você executa esse código, gerencie a seguinte exceção:</span><span class="sxs-lookup"><span data-stu-id="d2a23-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="d2a23-112">Para obter informações sobre as exceções que você pode esperar <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, e métodos de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> lançar, consulte a documentação de <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="d2a23-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  