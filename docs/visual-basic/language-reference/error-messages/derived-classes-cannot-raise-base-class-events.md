---
title: As classes derivadas não podem acionar eventos de classe base
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 7b86420466d77a6aa45b1201a9375b4433e4b5ec
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163435"
---
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a>BC30029: classes derivadas não podem gerar eventos de classe base

Um evento só pode ser gerado a partir do espaço de declaração no qual ele é declarado. Portanto, uma classe não pode gerar eventos de nenhuma outra classe, mesmo uma da qual ele é derivado.

 **ID do erro:** BC30029

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Mova a `Event` instrução ou a `RaiseEvent` instrução para que elas estejam na mesma classe.

## <a name="see-also"></a>Veja também

- [Instrução Event](../statements/event-statement.md)
- [Instrução RaiseEvent](../statements/raiseevent-statement.md)
