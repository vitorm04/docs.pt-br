---
title: Literais e propriedades de XML não são suportados em código inserido dentro do ASP.NET
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 893fdb1b9b3b5ace6b869c7b64ce7483ff523023
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403319"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>Literais e propriedades de XML não são suportados em código inserido dentro do ASP.NET
Não há suporte para literais XML e propriedades XML no código inserido dentro do ASP.NET. Para usar recursos XML, mova o código para code-behind.  
  
 Um literal XML ou uma propriedade de eixo XML é definida no código inserido (`<%= =>`) em um arquivo do ASP.NET.  
  
 **ID do erro:** BC31200  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mova o código que inclui a literal XML ou uma propriedade de eixo XML para um arquivo de code-behind do ASP.NET.  
  
## <a name="see-also"></a>Consulte também  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Propriedades do Eixo XML](../../../visual-basic/language-reference/xml-axis/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
