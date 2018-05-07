---
title: As classes derivadas não podem acionar eventos de classe base
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 365ce6ece1d964d3fac2a44f7ed4c1e16f44c95d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>As classes derivadas não podem acionar eventos de classe base
Um evento pode ser gerado somente do espaço de declaração no qual ela é declarada. Portanto, uma classe não pode disparar eventos de qualquer outra classe, até mesmo uma da qual ela é derivada.  
  
 **ID do erro:** BC30029  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mover o `Event` instrução ou o `RaiseEvent` instrução para que estejam na mesma classe.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
