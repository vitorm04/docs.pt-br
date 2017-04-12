---
title: "Estrutura &quot;&lt;structurename&gt;&quot; deve conter pelo menos uma variável de membro de instância ou declaração de evento de pelo menos uma instância não marcada como &quot;Custom&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30941
- vbc30941
dev_langs:
- VB
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: b73118bbfe707a1296998c91779811ec7c3e2aa3
ms.lasthandoff: 03/13/2017

---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>Estrutura '&lt;structurename&gt;' deve conter pelo menos uma variável de membro de instância ou declaração de evento de pelo menos uma instância não marcada como 'Custom'
Uma definição de estrutura não inclui quaisquer variáveis não compartilhadas ou eventos não personalizados não compartilhados.  
  
 Cada estrutura deve ter uma variável ou um evento que se aplica a cada instância específica (não compartilhada), em vez de para todas as instâncias coletivamente ([compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)). Não compartilhados constantes, propriedades e procedimentos não atender a esse requisito. Além disso, se houver há variáveis não compartilhadas e apenas um evento não compartilhado, este evento não pode ser um `Custom` eventos.  
  
 **ID do erro:** BC30941  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Defina pelo menos uma variável ou evento que não é `Shared`. Se você definir apenas um evento, ele deve ser não personalizados, bem como não compartilhado.  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Como: declarar uma estrutura](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
