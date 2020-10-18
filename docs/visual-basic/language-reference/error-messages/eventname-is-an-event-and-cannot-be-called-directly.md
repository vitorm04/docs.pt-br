---
title: "'<eventname>' é um evento, e não pode ser chamado diretamente"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 246cb92daa2c838c95f695542f33cf02af42764d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161979"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="12833-102">BC32022: ' \<eventname> ' é um evento e não pode ser chamado diretamente</span><span class="sxs-lookup"><span data-stu-id="12833-102">BC32022: '\<eventname>' is an event, and cannot be called directly</span></span>

<span data-ttu-id="12833-103">' <`eventname`> ' é um evento e, portanto, não pode ser chamado diretamente.</span><span class="sxs-lookup"><span data-stu-id="12833-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="12833-104">Use uma `RaiseEvent` instrução para gerar um evento.</span><span class="sxs-lookup"><span data-stu-id="12833-104">Use a `RaiseEvent` statement to raise an event.</span></span>

 <span data-ttu-id="12833-105">Uma chamada de procedimento especifica um evento para o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="12833-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="12833-106">Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo de sinalização, que deve ser gerado e manipulado.</span><span class="sxs-lookup"><span data-stu-id="12833-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>

 <span data-ttu-id="12833-107">**ID do erro:** BC32022</span><span class="sxs-lookup"><span data-stu-id="12833-107">**Error ID:** BC32022</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="12833-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="12833-108">To correct this error</span></span>

- <span data-ttu-id="12833-109">Use uma `RaiseEvent` instrução para sinalizar um evento e invocar o procedimento ou procedimentos que o manipulam.</span><span class="sxs-lookup"><span data-stu-id="12833-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>

## <a name="see-also"></a><span data-ttu-id="12833-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="12833-110">See also</span></span>

- [<span data-ttu-id="12833-111">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="12833-111">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
