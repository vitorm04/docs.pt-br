---
title: "Instruções &quot;#Region&quot; e &quot;#End Region&quot; não são válidas dentro lambdas multilinha corpos de método | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32025
- vbc32025
dev_langs:
- VB
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: 10
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
ms.openlocfilehash: 556f88d4232efffae5c852f8a151cbc18858f9b3
ms.lasthandoff: 03/13/2017

---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>Instruções '#Region' e '#End Region' não são válidas dentro do método corpos/lambdas multilinha
O `#Region` bloco deve ser declarado em um nível de classe, módulo ou namespace. Uma região recolhível pode incluir um ou mais procedimentos, mas ele não pode começar ou terminar dentro de um procedimento.  
  
 **ID do erro:** BC32025  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que o procedimento anterior é encerrado corretamente com um `End Function` ou `End Sub` instrução.  
  
2.  Verifique se o `#Region` e `#End Region` diretivas estão no mesmo bloco de código.  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
