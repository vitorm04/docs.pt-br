---
title: "Classes derivadas não podem elevar eventos de classe base | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
dev_langs:
- VB
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4dc36d182e036c1c7fb7873a33436ec594f1bc2c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="ec975-102">As classes derivadas não podem acionar eventos de classe base</span><span class="sxs-lookup"><span data-stu-id="ec975-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="ec975-103">Um evento pode ser gerado apenas do espaço de declaração na qual ela é declarada.</span><span class="sxs-lookup"><span data-stu-id="ec975-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="ec975-104">Portanto, uma classe não pode disparar eventos de qualquer outra classe, até mesmo uma da qual ela é derivada.</span><span class="sxs-lookup"><span data-stu-id="ec975-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="ec975-105">**ID do erro:** BC30029</span><span class="sxs-lookup"><span data-stu-id="ec975-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ec975-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ec975-106">To correct this error</span></span>  
  
-   <span data-ttu-id="ec975-107">Mova o `Event` instrução ou o `RaiseEvent` instrução para que estejam na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="ec975-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec975-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec975-108">See Also</span></span>  
 <span data-ttu-id="ec975-109">[Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ec975-109">[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="ec975-110"> [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)</span><span class="sxs-lookup"><span data-stu-id="ec975-110"> [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md)</span></span>
