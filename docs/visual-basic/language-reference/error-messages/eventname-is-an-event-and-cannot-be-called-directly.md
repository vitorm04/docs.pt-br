---
title: "'<eventname>' é um evento, e não pode ser chamado diretamente"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 4e27d9ce788ae7b9741c0cb80da776959748b8b9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272709"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="feb4a-102">'\<eventname >' é um evento e não pode ser chamado diretamente</span><span class="sxs-lookup"><span data-stu-id="feb4a-102">'\<eventname>' is an event, and cannot be called directly</span></span>
<span data-ttu-id="feb4a-103">' <`eventname`>' é um evento e, portanto, não pode ser chamado diretamente.</span><span class="sxs-lookup"><span data-stu-id="feb4a-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="feb4a-104">Use um `RaiseEvent` instrução acionar um evento.</span><span class="sxs-lookup"><span data-stu-id="feb4a-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="feb4a-105">Uma chamada de procedimento especifica um evento para o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="feb4a-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="feb4a-106">Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo de sinalização, que deve ser gerado e manipulado.</span><span class="sxs-lookup"><span data-stu-id="feb4a-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="feb4a-107">**ID do erro:** BC32022</span><span class="sxs-lookup"><span data-stu-id="feb4a-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="feb4a-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="feb4a-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="feb4a-109">Use um `RaiseEvent` instrução para sinalizar um evento e chamar o procedimento ou procedimentos que lidam com ele.</span><span class="sxs-lookup"><span data-stu-id="feb4a-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb4a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="feb4a-110">See also</span></span>
- [<span data-ttu-id="feb4a-111">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="feb4a-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
