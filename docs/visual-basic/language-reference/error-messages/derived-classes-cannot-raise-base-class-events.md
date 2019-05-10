---
title: As classes derivadas não podem acionar eventos de classe base
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 030c9c2ffa97572298b23f05c23e3af0df7387b0
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913170"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>As classes derivadas não podem acionar eventos de classe base
Um evento pode ser gerado apenas do espaço de declaração na qual ela é declarada. Portanto, uma classe não pode gerar eventos de qualquer outra classe, mesmo um do qual ele é derivado.  
  
 **ID do erro:** BC30029  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Mover o `Event` instrução ou o `RaiseEvent` instrução para que estejam na mesma classe.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
