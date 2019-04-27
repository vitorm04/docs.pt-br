---
title: As classes derivadas não podem acionar eventos de classe base
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0e9acf4b3e71295655c15ae9b1c80852c9aca8df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803565"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>As classes derivadas não podem acionar eventos de classe base
Um evento pode ser gerado apenas do espaço de declaração na qual ela é declarada. Portanto, uma classe não pode gerar eventos de qualquer outra classe, mesmo um do qual ele é derivado.  
  
 **ID do erro:** BC30029  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mover o `Event` instrução ou o `RaiseEvent` instrução para que estejam na mesma classe.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
