---
title: Instrução AddHandler
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07fbfe04ccd01b7d0f99338ef2682238830099dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="addhandler-statement"></a><span data-ttu-id="14138-102">Instrução AddHandler</span><span class="sxs-lookup"><span data-stu-id="14138-102">AddHandler Statement</span></span>
<span data-ttu-id="14138-103">Associa um evento com um manipulador de eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="14138-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14138-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14138-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="14138-105">Partes</span><span class="sxs-lookup"><span data-stu-id="14138-105">Parts</span></span>  
 `event`  
 <span data-ttu-id="14138-106">O nome do evento para manipular.</span><span class="sxs-lookup"><span data-stu-id="14138-106">The name of the event to handle.</span></span>  
  
 `eventhandler`  
 <span data-ttu-id="14138-107">O nome de um procedimento que manipula o evento.</span><span class="sxs-lookup"><span data-stu-id="14138-107">The name of a procedure that handles the event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14138-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="14138-108">Remarks</span></span>  
 <span data-ttu-id="14138-109">O `AddHandler` e `RemoveHandler` instruções permitem iniciar e interromper a manipulação de eventos a qualquer momento durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="14138-109">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="14138-110">A assinatura do `eventhandler` procedimento deve corresponder à assinatura do evento `event`.</span><span class="sxs-lookup"><span data-stu-id="14138-110">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="14138-111">O `Handles` palavra-chave e o `AddHandler` instrução ambos permitem que você especifique que determinados procedimentos manipulem eventos específicos, mas há diferenças.</span><span class="sxs-lookup"><span data-stu-id="14138-111">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="14138-112">O `AddHandler` instrução conecta os procedimentos a eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="14138-112">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="14138-113">Use o `Handles` palavra-chave ao definir um procedimento para especificar que ele manipula um evento específico.</span><span class="sxs-lookup"><span data-stu-id="14138-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="14138-114">Para obter mais informações, consulte [manipula](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="14138-114">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14138-115">Para eventos personalizados, o `AddHandler` instrução invoca o evento `AddHandler` acessador.</span><span class="sxs-lookup"><span data-stu-id="14138-115">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="14138-116">Para obter mais informações sobre eventos personalizados, consulte [instrução Event](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="14138-116">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14138-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="14138-117">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="14138-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14138-118">See Also</span></span>  
 [<span data-ttu-id="14138-119">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="14138-119">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="14138-120">Handles</span><span class="sxs-lookup"><span data-stu-id="14138-120">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="14138-121">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="14138-121">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="14138-122">Eventos</span><span class="sxs-lookup"><span data-stu-id="14138-122">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
