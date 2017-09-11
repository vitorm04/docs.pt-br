---
title: "&quot;&lt;eventname&gt;&quot; é um evento e não pode ser chamado diretamente | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32022
- vbc32022
dev_langs:
- VB
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
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
ms.openlocfilehash: aaca16d5c33a4adcb8cbd16477a7c46e136622a9
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="4ee9d-102">'&lt;eventname&gt;' é um evento e não pode ser chamado diretamente</span><span class="sxs-lookup"><span data-stu-id="4ee9d-102">&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly</span></span>
<span data-ttu-id="4ee9d-103">'`eventname`>' é um evento e por isso não pode ser chamado diretamente.</span><span class="sxs-lookup"><span data-stu-id="4ee9d-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="4ee9d-104">Use um `RaiseEvent` instrução para disparar um evento.</span><span class="sxs-lookup"><span data-stu-id="4ee9d-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="4ee9d-105">Uma chamada de procedimento especifica um evento para o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="4ee9d-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="4ee9d-106">Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo de sinalização, que deve ser gerado e manipulado.</span><span class="sxs-lookup"><span data-stu-id="4ee9d-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="4ee9d-107">**ID do erro:** BC32022</span><span class="sxs-lookup"><span data-stu-id="4ee9d-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4ee9d-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4ee9d-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="4ee9d-109">Use um `RaiseEvent` instrução para sinalizar um evento e chamar o procedimento ou procedimentos que lidam com ele.</span><span class="sxs-lookup"><span data-stu-id="4ee9d-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ee9d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ee9d-110">See Also</span></span>  
 [<span data-ttu-id="4ee9d-111">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="4ee9d-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
