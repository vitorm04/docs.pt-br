---
title: "As classes derivadas não podem acionar eventos de classe base"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords: BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="98449-102">As classes derivadas não podem acionar eventos de classe base</span><span class="sxs-lookup"><span data-stu-id="98449-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="98449-103">Um evento pode ser gerado somente do espaço de declaração no qual ela é declarada.</span><span class="sxs-lookup"><span data-stu-id="98449-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="98449-104">Portanto, uma classe não pode disparar eventos de qualquer outra classe, até mesmo uma da qual ela é derivada.</span><span class="sxs-lookup"><span data-stu-id="98449-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="98449-105">**ID do erro:** BC30029</span><span class="sxs-lookup"><span data-stu-id="98449-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="98449-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="98449-106">To correct this error</span></span>  
  
-   <span data-ttu-id="98449-107">Mover o `Event` instrução ou o `RaiseEvent` instrução para que estejam na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="98449-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98449-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98449-108">See Also</span></span>  
 [<span data-ttu-id="98449-109">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="98449-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="98449-110">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="98449-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
