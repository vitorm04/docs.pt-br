---
title: Instrução AddHandler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: f731ff150bd901e325726fca5aa682ff1770f979
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396481"
---
# <a name="addhandler-statement"></a><span data-ttu-id="98f19-102">Instrução AddHandler</span><span class="sxs-lookup"><span data-stu-id="98f19-102">AddHandler Statement</span></span>
<span data-ttu-id="98f19-103">Associa um evento com um manipulador de eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="98f19-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98f19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98f19-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="98f19-105">Partes</span><span class="sxs-lookup"><span data-stu-id="98f19-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="98f19-106">evento</span><span class="sxs-lookup"><span data-stu-id="98f19-106">event</span></span>|<span data-ttu-id="98f19-107">O nome do evento para manipular.</span><span class="sxs-lookup"><span data-stu-id="98f19-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="98f19-108">O nome de um procedimento que manipula o evento.</span><span class="sxs-lookup"><span data-stu-id="98f19-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="98f19-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="98f19-109">Remarks</span></span>  
 <span data-ttu-id="98f19-110">O `AddHandler` e `RemoveHandler` instruções permitem que você inicie e pare a manipulação de eventos a qualquer momento durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="98f19-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="98f19-111">A assinatura do `eventhandler` procedimento deve corresponder à assinatura do evento `event`.</span><span class="sxs-lookup"><span data-stu-id="98f19-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="98f19-112">O `Handles` palavra-chave e o `AddHandler` instrução os dois permitem que você especifique que determinados procedimentos manipulem eventos específicos, mas há diferenças.</span><span class="sxs-lookup"><span data-stu-id="98f19-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="98f19-113">O `AddHandler` instrução conecta os procedimentos a eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="98f19-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="98f19-114">Use o `Handles` palavra-chave ao definir um procedimento para especificar que ele manipula um evento específico.</span><span class="sxs-lookup"><span data-stu-id="98f19-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="98f19-115">Para obter mais informações, consulte [manipula](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="98f19-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98f19-116">Para eventos personalizados, o `AddHandler` instrução invoca o evento `AddHandler` acessador.</span><span class="sxs-lookup"><span data-stu-id="98f19-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="98f19-117">Para obter mais informações sobre eventos personalizados, consulte [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="98f19-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98f19-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98f19-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="98f19-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98f19-119">See Also</span></span>  
 [<span data-ttu-id="98f19-120">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="98f19-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="98f19-121">Handles</span><span class="sxs-lookup"><span data-stu-id="98f19-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="98f19-122">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="98f19-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="98f19-123">Eventos</span><span class="sxs-lookup"><span data-stu-id="98f19-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
