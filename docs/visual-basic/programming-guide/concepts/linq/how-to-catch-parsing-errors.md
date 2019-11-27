---
title: 'Como: Erros de análise de captura'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: 14c4f76c5f10616f9346084cda276e2862b2b41d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353352"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="b1b79-102">Como: capturar erros de análise (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1b79-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="b1b79-103">Este tópico mostra como detectar XML mal formado ou inválido.</span><span class="sxs-lookup"><span data-stu-id="b1b79-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="b1b79-104">é implementado usando <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="b1b79-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="b1b79-105">Se malformado ou XML válido é passado para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], a classe subjacente de <xref:System.Xml.XmlReader> irá acionar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b1b79-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="b1b79-106">Os vários métodos que analisam XML, tais como <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, não capturam a exceção; a exceção pode ser capturada por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1b79-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="b1b79-107">Observe que você não pode obter análise erros se você usar literais XML.</span><span class="sxs-lookup"><span data-stu-id="b1b79-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="b1b79-108">O compilador do Visual Basic irá capturar erros de XML mal formado ou inválido.</span><span class="sxs-lookup"><span data-stu-id="b1b79-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1b79-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1b79-109">Example</span></span>  
 <span data-ttu-id="b1b79-110">O código a seguir tenta analisar XML válido:</span><span class="sxs-lookup"><span data-stu-id="b1b79-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="b1b79-111">Quando você executa esse código, gerencie a seguinte exceção:</span><span class="sxs-lookup"><span data-stu-id="b1b79-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="b1b79-112">Para obter informações sobre as exceções que você pode esperar <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, e métodos de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> lançar, consulte a documentação de <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="b1b79-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1b79-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1b79-113">See also</span></span>

- [<span data-ttu-id="b1b79-114">Analisando XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1b79-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
