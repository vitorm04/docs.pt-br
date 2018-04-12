---
title: Literais e propriedades de XML não são suportados em código inserido dentro do ASP.NET
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 932c36778720718d777412f958c16b4a650e3b5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>Literais e propriedades de XML não são suportados em código inserido dentro do ASP.NET
Não há suporte para literais XML e propriedades XML no código inserido dentro do ASP.NET. Para usar os recursos XML, mova o código para code-behind.  
  
 Um literal XML ou propriedade de eixo XML é definida no código inserido (`<%= =>`) em um arquivo do ASP.NET.  
  
 **ID do erro:** BC31200  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mova o código que inclui o literal XML ou propriedade de eixo XML para um arquivo de code-behind do ASP.NET.  
  
## <a name="see-also"></a>Consulte também  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Propriedades do Eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
