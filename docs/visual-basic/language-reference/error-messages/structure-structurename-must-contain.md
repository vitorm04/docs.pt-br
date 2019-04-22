---
title: A estrutura '<structurename>' deve conter pelos menos uma variável membro da instância ou pelo menos uma declaração de evento da instância não marcada como 'Personalizada'
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 598aef3943a53ee6eb97064819c9128de1839f52
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813932"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>Estrutura '\<structurename >' deve conter pelo menos uma variável de membro de instância ou declaração de evento de pelo menos uma instância não marcada como 'Personalizada'
Uma definição de estrutura não inclui quaisquer variáveis não compartilhadas ou eventos não personalizados não compartilhados.  
  
 Cada estrutura deve ter uma variável ou um evento que se aplica a cada instância específica (não compartilhada) em vez da todas as instâncias coletivamente ([compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)). Não compartilhado de constantes, propriedades e procedimentos não atendem a esse requisito. Além disso, se não houver nenhuma variáveis não compartilhadas e apenas um evento não compartilhado, esse evento não pode ser um `Custom` eventos.  
  
 **ID do erro:** BC30941  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Defina pelo menos uma variável ou evento que não é `Shared`. Se você definir apenas um evento, ele deve ser não personalizados, bem como não compartilhado.  
  
## <a name="see-also"></a>Consulte também

- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Como: declarar uma estrutura](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
