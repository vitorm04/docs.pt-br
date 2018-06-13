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
ms.locfileid: "33586393"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="2fd35-102">As classes derivadas não podem acionar eventos de classe base</span><span class="sxs-lookup"><span data-stu-id="2fd35-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="2fd35-103">Um evento pode ser gerado somente do espaço de declaração no qual ela é declarada.</span><span class="sxs-lookup"><span data-stu-id="2fd35-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="2fd35-104">Portanto, uma classe não pode disparar eventos de qualquer outra classe, até mesmo uma da qual ela é derivada.</span><span class="sxs-lookup"><span data-stu-id="2fd35-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="2fd35-105">**ID do erro:** BC30029</span><span class="sxs-lookup"><span data-stu-id="2fd35-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2fd35-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2fd35-106">To correct this error</span></span>  
  
-   <span data-ttu-id="2fd35-107">Mover o `Event` instrução ou o `RaiseEvent` instrução para que estejam na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="2fd35-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd35-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fd35-108">See Also</span></span>  
 [<span data-ttu-id="2fd35-109">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="2fd35-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="2fd35-110">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="2fd35-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
