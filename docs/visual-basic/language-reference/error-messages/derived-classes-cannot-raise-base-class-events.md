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
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="b6037-102">As classes derivadas não podem acionar eventos de classe base</span><span class="sxs-lookup"><span data-stu-id="b6037-102">Derived classes cannot raise base class events</span></span>

<span data-ttu-id="b6037-103">Um evento só pode ser gerado a partir do espaço de declaração no qual ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="b6037-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="b6037-104">Portanto, uma classe não pode gerar eventos de nenhuma outra classe, mesmo uma da qual ele é derivado.</span><span class="sxs-lookup"><span data-stu-id="b6037-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="b6037-105">**ID do erro:** BC30029</span><span class="sxs-lookup"><span data-stu-id="b6037-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b6037-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b6037-106">To correct this error</span></span>  
  
- <span data-ttu-id="b6037-107">Mova a `Event` instrução ou a `RaiseEvent` instrução para que elas estejam na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="b6037-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6037-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="b6037-108">See also</span></span>

- [<span data-ttu-id="b6037-109">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="b6037-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="b6037-110">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="b6037-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
