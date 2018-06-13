---
title: Literais e propriedades de XML não são suportados em código inserido dentro do ASP.NET
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 559889587b30418dc2fe2860cfbf90f91605c668
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594836"
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
