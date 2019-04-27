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
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="827e0-102">As classes derivadas não podem acionar eventos de classe base</span><span class="sxs-lookup"><span data-stu-id="827e0-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="827e0-103">Um evento pode ser gerado apenas do espaço de declaração na qual ela é declarada.</span><span class="sxs-lookup"><span data-stu-id="827e0-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="827e0-104">Portanto, uma classe não pode gerar eventos de qualquer outra classe, mesmo um do qual ele é derivado.</span><span class="sxs-lookup"><span data-stu-id="827e0-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="827e0-105">**ID do erro:** BC30029</span><span class="sxs-lookup"><span data-stu-id="827e0-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="827e0-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="827e0-106">To correct this error</span></span>  
  
-   <span data-ttu-id="827e0-107">Mover o `Event` instrução ou o `RaiseEvent` instrução para que estejam na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="827e0-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="827e0-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="827e0-108">See also</span></span>

- [<span data-ttu-id="827e0-109">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="827e0-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="827e0-110">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="827e0-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
