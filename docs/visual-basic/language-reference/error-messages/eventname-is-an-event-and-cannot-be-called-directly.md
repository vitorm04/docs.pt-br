---
title: "&#39; &lt;eventname&gt;&#39; é um evento e não pode ser chamado diretamente"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords: BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb987c957a28aa37c40ad975b945c20da4690f6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="2f906-102">&#39; &lt;eventname&gt;&#39; é um evento e não pode ser chamado diretamente</span><span class="sxs-lookup"><span data-stu-id="2f906-102">&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly</span></span>
<span data-ttu-id="2f906-103">' <`eventname`>' é um evento e portanto não pode ser chamado diretamente.</span><span class="sxs-lookup"><span data-stu-id="2f906-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="2f906-104">Use um `RaiseEvent` instrução para gerar um evento.</span><span class="sxs-lookup"><span data-stu-id="2f906-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="2f906-105">Uma chamada de procedimento especifica um evento para o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="2f906-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="2f906-106">Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo sinalizador, que deve ser gerado e manipulado.</span><span class="sxs-lookup"><span data-stu-id="2f906-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="2f906-107">**ID do erro:** BC32022</span><span class="sxs-lookup"><span data-stu-id="2f906-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2f906-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2f906-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="2f906-109">Use um `RaiseEvent` instrução para sinalizar um evento e chamar o procedimento ou procedimentos que lidam com ele.</span><span class="sxs-lookup"><span data-stu-id="2f906-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f906-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f906-110">See Also</span></span>  
 [<span data-ttu-id="2f906-111">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="2f906-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
