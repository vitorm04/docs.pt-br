---
title: '&#39;&lt;EventName&gt; &#39; é um evento e não pode ser chamado diretamente'
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 3efd8c18497ce288e16659db4ca4693d5a3e6acc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581977"
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="0a7a7-102">&#39;&lt;EventName&gt; &#39; é um evento e não pode ser chamado diretamente</span><span class="sxs-lookup"><span data-stu-id="0a7a7-102">&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly</span></span>
<span data-ttu-id="0a7a7-103">' <`eventname`>' é um evento e, portanto, não pode ser chamado diretamente.</span><span class="sxs-lookup"><span data-stu-id="0a7a7-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="0a7a7-104">Use um `RaiseEvent` instrução acionar um evento.</span><span class="sxs-lookup"><span data-stu-id="0a7a7-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="0a7a7-105">Uma chamada de procedimento especifica um evento para o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="0a7a7-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="0a7a7-106">Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo de sinalização, que deve ser gerado e manipulado.</span><span class="sxs-lookup"><span data-stu-id="0a7a7-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="0a7a7-107">**ID do erro:** BC32022</span><span class="sxs-lookup"><span data-stu-id="0a7a7-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a7a7-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0a7a7-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="0a7a7-109">Use um `RaiseEvent` instrução para sinalizar um evento e chamar o procedimento ou procedimentos que lidam com ele.</span><span class="sxs-lookup"><span data-stu-id="0a7a7-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a7a7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a7a7-110">See also</span></span>
- [<span data-ttu-id="0a7a7-111">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="0a7a7-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
