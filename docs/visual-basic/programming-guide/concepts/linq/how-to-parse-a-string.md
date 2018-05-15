---
title: 'Como: analisar uma cadeia de caracteres (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: da12ec98e03acceae375bbed4fc6ad4c2a71ec2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="2a248-102">Como: analisar uma cadeia de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a248-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="2a248-103">Este tópico mostra como criar uma árvore XML em c#.</span><span class="sxs-lookup"><span data-stu-id="2a248-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a248-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a248-104">Example</span></span>  
 <span data-ttu-id="2a248-105">Você pode analisar uma cadeia de caracteres no Visual Basic usando o `XElement.Parse` método.</span><span class="sxs-lookup"><span data-stu-id="2a248-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="2a248-106">No entanto, é mais eficiente usar literais XML, conforme mostrado no código a seguir, porque literais XML não tem as mesmo penalidades de desempenho como análise de XML de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2a248-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="2a248-107">Usando literais XML, você pode apenas copiar e colar o XML em seu programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2a248-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a248-108">Analisar texto ou carregar um documento XML de um arquivo de texto é menos eficiente do que a construção funcional.</span><span class="sxs-lookup"><span data-stu-id="2a248-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="2a248-109">Se você estiver inicializando uma árvore XML de código, o tempo do processador é menor para usar a construção funcional do que para analisar texto.</span><span class="sxs-lookup"><span data-stu-id="2a248-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a248-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a248-110">See Also</span></span>  
 [<span data-ttu-id="2a248-111">Análise de XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a248-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
