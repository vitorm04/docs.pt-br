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
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="713e1-102">As classes derivadas não podem acionar eventos de classe base</span><span class="sxs-lookup"><span data-stu-id="713e1-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="713e1-103">Um evento pode ser gerado apenas do espaço de declaração na qual ela é declarada.</span><span class="sxs-lookup"><span data-stu-id="713e1-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="713e1-104">Portanto, uma classe não pode gerar eventos de qualquer outra classe, mesmo um do qual ele é derivado.</span><span class="sxs-lookup"><span data-stu-id="713e1-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="713e1-105">**ID do erro:** BC30029</span><span class="sxs-lookup"><span data-stu-id="713e1-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="713e1-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="713e1-106">To correct this error</span></span>  
  
- <span data-ttu-id="713e1-107">Mover o `Event` instrução ou o `RaiseEvent` instrução para que estejam na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="713e1-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713e1-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="713e1-108">See also</span></span>

- [<span data-ttu-id="713e1-109">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="713e1-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="713e1-110">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="713e1-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
