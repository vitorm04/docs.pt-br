---
title: "'<eventname>' é um evento, e não pode ser chamado diretamente"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: bf900566bdb4ecf8d8961a12b5dd67ba426caf27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305592"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="156b3-102">'\<eventname >' é um evento e não pode ser chamado diretamente</span><span class="sxs-lookup"><span data-stu-id="156b3-102">'\<eventname>' is an event, and cannot be called directly</span></span>
<span data-ttu-id="156b3-103">' <`eventname`>' é um evento e, portanto, não pode ser chamado diretamente.</span><span class="sxs-lookup"><span data-stu-id="156b3-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="156b3-104">Use um `RaiseEvent` instrução acionar um evento.</span><span class="sxs-lookup"><span data-stu-id="156b3-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="156b3-105">Uma chamada de procedimento especifica um evento para o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="156b3-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="156b3-106">Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo de sinalização, que deve ser gerado e manipulado.</span><span class="sxs-lookup"><span data-stu-id="156b3-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="156b3-107">**ID do erro:** BC32022</span><span class="sxs-lookup"><span data-stu-id="156b3-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="156b3-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="156b3-108">To correct this error</span></span>  
  
1. <span data-ttu-id="156b3-109">Use um `RaiseEvent` instrução para sinalizar um evento e chamar o procedimento ou procedimentos que lidam com ele.</span><span class="sxs-lookup"><span data-stu-id="156b3-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="156b3-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="156b3-110">See also</span></span>

- [<span data-ttu-id="156b3-111">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="156b3-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
