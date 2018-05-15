---
title: '&#39;&lt;EventName&gt; &#39; é um evento e não pode ser chamado diretamente'
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 4d8a7d716d2b7c52d1d027a1e7959d981bb0857e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="67f12-102">&#39;&lt;EventName&gt; &#39; é um evento e não pode ser chamado diretamente</span><span class="sxs-lookup"><span data-stu-id="67f12-102">&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly</span></span>
<span data-ttu-id="67f12-103">' <`eventname`>' é um evento e portanto não pode ser chamado diretamente.</span><span class="sxs-lookup"><span data-stu-id="67f12-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="67f12-104">Use um `RaiseEvent` instrução para gerar um evento.</span><span class="sxs-lookup"><span data-stu-id="67f12-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="67f12-105">Uma chamada de procedimento especifica um evento para o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="67f12-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="67f12-106">Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo sinalizador, que deve ser gerado e manipulado.</span><span class="sxs-lookup"><span data-stu-id="67f12-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="67f12-107">**ID do erro:** BC32022</span><span class="sxs-lookup"><span data-stu-id="67f12-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="67f12-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="67f12-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="67f12-109">Use um `RaiseEvent` instrução para sinalizar um evento e chamar o procedimento ou procedimentos que lidam com ele.</span><span class="sxs-lookup"><span data-stu-id="67f12-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f12-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67f12-110">See Also</span></span>  
 [<span data-ttu-id="67f12-111">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="67f12-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
