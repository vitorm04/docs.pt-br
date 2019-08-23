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
ms.openlocfilehash: a9913cd682e52562422ba140e27187d37c592684
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928948"
---
# <a name="addhandler-statement"></a><span data-ttu-id="e6253-102">Instrução AddHandler</span><span class="sxs-lookup"><span data-stu-id="e6253-102">AddHandler Statement</span></span>
<span data-ttu-id="e6253-103">Associa um evento a um manipulador de eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e6253-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6253-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6253-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="e6253-105">Partes</span><span class="sxs-lookup"><span data-stu-id="e6253-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="e6253-106">evento</span><span class="sxs-lookup"><span data-stu-id="e6253-106">event</span></span>|<span data-ttu-id="e6253-107">O nome do evento a ser manipulado.</span><span class="sxs-lookup"><span data-stu-id="e6253-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="e6253-108">O nome de um procedimento que manipula o evento.</span><span class="sxs-lookup"><span data-stu-id="e6253-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="e6253-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6253-109">Remarks</span></span>  
 <span data-ttu-id="e6253-110">As `AddHandler` instruções `RemoveHandler` e permitem iniciar e parar a manipulação de eventos a qualquer momento durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="e6253-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="e6253-111">A assinatura do `eventhandler` procedimento deve corresponder à assinatura do evento `event`.</span><span class="sxs-lookup"><span data-stu-id="e6253-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="e6253-112">A `Handles` palavra-chave `AddHandler` e a instrução permitem que você especifique que procedimentos específicos manipulam eventos específicos, mas há diferenças.</span><span class="sxs-lookup"><span data-stu-id="e6253-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="e6253-113">A `AddHandler` instrução conecta procedimentos a eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e6253-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="e6253-114">Use a `Handles` palavra-chave ao definir um procedimento para especificar que ele trata de um evento específico.</span><span class="sxs-lookup"><span data-stu-id="e6253-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="e6253-115">Para obter mais informações, consulte [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e6253-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6253-116">Para eventos personalizados, a `AddHandler` instrução invoca o acessador `AddHandler` do evento.</span><span class="sxs-lookup"><span data-stu-id="e6253-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="e6253-117">Para obter mais informações sobre eventos personalizados, consulte [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e6253-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6253-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e6253-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="e6253-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6253-119">See also</span></span>

- [<span data-ttu-id="e6253-120">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="e6253-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="e6253-121">Handles</span><span class="sxs-lookup"><span data-stu-id="e6253-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="e6253-122">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="e6253-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="e6253-123">Eventos</span><span class="sxs-lookup"><span data-stu-id="e6253-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
