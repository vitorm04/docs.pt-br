---
title: 'Como: Capturar erros de análise (C#)'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 2f56ca48278f9ad8b38f8564f54a379cc09f94ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515856"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="63736-102">Como: Capturar erros de análise (C#)</span><span class="sxs-lookup"><span data-stu-id="63736-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="63736-103">Este tópico mostra como detectar XML mal formado ou inválido.</span><span class="sxs-lookup"><span data-stu-id="63736-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="63736-104">é implementado usando <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="63736-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="63736-105">Se malformado ou XML válido é passado para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], a classe subjacente de <xref:System.Xml.XmlReader> irá acionar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="63736-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="63736-106">Os vários métodos que analisam XML, tais como <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, não capturam a exceção; a exceção pode ser capturada por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63736-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63736-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="63736-107">Example</span></span>  
 <span data-ttu-id="63736-108">O código a seguir tenta analisar XML válido:</span><span class="sxs-lookup"><span data-stu-id="63736-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="63736-109">Quando você executa esse código, gerencie a seguinte exceção:</span><span class="sxs-lookup"><span data-stu-id="63736-109">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="63736-110">Para obter informações sobre as exceções que você pode esperar <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, e métodos de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> lançar, consulte a documentação de <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="63736-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63736-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63736-111">See also</span></span>

- [<span data-ttu-id="63736-112">Analisando XML (C#)</span><span class="sxs-lookup"><span data-stu-id="63736-112">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
