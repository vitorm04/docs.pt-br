---
title: Estrutura &#39; &lt;structurename&gt;&#39; deve conter a variável de membro de pelo menos uma instância ou declaração de evento de pelo menos uma instância não marcada como &#39; Personalizar &#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b28dd59271bdaca52072710ea797fae6e9168eab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>Estrutura &#39; &lt;structurename&gt;&#39; deve conter a variável de membro de pelo menos uma instância ou declaração de evento de pelo menos uma instância não marcada como &#39; Personalizar &#39;
Uma definição de estrutura não inclui quaisquer variáveis não compartilhadas ou eventos não personalizados não compartilhados.  
  
 Cada estrutura deve ter uma variável ou um evento que se aplica a cada instância específica (compartilhada), em vez de para todas as instâncias coletivamente ([compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)). Procedimentos, propriedades e constantes não compartilhados não atender a esse requisito. Além disso, se não houver nenhum variáveis não compartilhadas e apenas um evento não compartilhado, este evento não pode ser um `Custom` eventos.  
  
 **ID do erro:** BC30941  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Defina pelo menos uma variável ou evento que não é `Shared`. Se você definir apenas um evento, ele deve ser não personalizados, bem como não compartilhado.  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Como declarar uma estrutura](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
