---
title: As classes derivadas não podem acionar eventos de classe base
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0233a1584c5e871506b5c4762e98874c343f19b8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874489"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>As classes derivadas não podem acionar eventos de classe base

Um evento só pode ser gerado a partir do espaço de declaração no qual ele é declarado. Portanto, uma classe não pode gerar eventos de nenhuma outra classe, mesmo uma da qual ele é derivado.  
  
 **ID do erro:** BC30029  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Mova a `Event` instrução ou a `RaiseEvent` instrução para que elas estejam na mesma classe.  
  
## <a name="see-also"></a>Confira também

- [Instrução Event](../statements/event-statement.md)
- [Instrução RaiseEvent](../statements/raiseevent-statement.md)
