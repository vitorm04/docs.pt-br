---
title: 'Como: analisar uma cadeia de caracteres (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d0fd7c7adcfbd7e2136d1a652017d470634016b9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-parse-a-string-visual-basic"></a>Como: analisar uma cadeia de caracteres (Visual Basic)
Este tópico mostra como criar uma árvore XML em c#.  
  
## <a name="example"></a>Exemplo  
 Você pode analisar uma cadeia de caracteres no Visual Basic usando o `XElement.Parse` método. No entanto, é mais eficiente usar literais XML, conforme mostrado no código a seguir, porque literais XML não tem as mesmo penalidades de desempenho como análise de XML de uma cadeia de caracteres.  
  
 Usando literais XML, você pode apenas copiar e colar o XML em seu programa Visual Basic.  
  
> [!NOTE]
>  Analisar texto ou carregar um documento XML de um arquivo de texto é menos eficiente do que a construção funcional. Se você estiver inicializando uma árvore XML de código, o tempo do processador é menor para usar a construção funcional do que para analisar texto.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Análise de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
