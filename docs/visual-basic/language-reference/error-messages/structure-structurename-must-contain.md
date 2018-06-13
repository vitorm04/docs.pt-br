---
title: Estrutura &#39; &lt;structurename&gt; &#39; deve conter pelo menos uma variável de membro de instância ou declaração de evento de pelo menos uma instância não marcada como &#39;personalizado&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 85a4babc808e274a99f2c9faf08a02abf8aa4e93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594491"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>Estrutura &#39; &lt;structurename&gt; &#39; deve conter pelo menos uma variável de membro de instância ou declaração de evento de pelo menos uma instância não marcada como &#39;personalizado&#39;
Uma definição de estrutura não inclui quaisquer variáveis não compartilhadas ou eventos não personalizados não compartilhados.  
  
 Cada estrutura deve ter uma variável ou um evento que se aplica a cada instância específica (compartilhada), em vez de para todas as instâncias coletivamente ([compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)). Procedimentos, propriedades e constantes não compartilhados não atender a esse requisito. Além disso, se não houver nenhum variáveis não compartilhadas e apenas um evento não compartilhado, este evento não pode ser um `Custom` eventos.  
  
 **ID do erro:** BC30941  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Defina pelo menos uma variável ou evento que não é `Shared`. Se você definir apenas um evento, ele deve ser não personalizados, bem como não compartilhado.  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Como declarar uma estrutura](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
