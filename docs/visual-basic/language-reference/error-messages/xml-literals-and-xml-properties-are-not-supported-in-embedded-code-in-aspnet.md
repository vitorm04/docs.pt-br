---
title: "Não há suporte para literais XML e propriedades XML no código incorporado no ASP.NET | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31200
- bc31200
dev_langs:
- VB
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3264545fea1d81d141696d4001b35aa1bd926568
ms.lasthandoff: 03/13/2017

---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>Literais e propriedades de XML não são suportados em código inserido dentro do ASP.NET
Não há suporte para literais XML e propriedades XML no código incorporado no ASP.NET. Para usar recursos XML, mova o código para code-behind.  
  
 Um literal XML ou propriedade de eixo XML é definida no código incorporado (`<%= =>`) em um arquivo do ASP.NET.  
  
 **ID do erro:** BC31200  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mova o código que inclui o literal XML ou propriedade de eixo XML para um arquivo de code-behind do ASP.NET.  
  
## <a name="see-also"></a>Consulte também  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
