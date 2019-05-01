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
ms.openlocfilehash: 1e8d8f512f163d82f074a5ad53fbb38a10904dfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054296"
---
# <a name="addhandler-statement"></a><span data-ttu-id="f438b-102">Instrução AddHandler</span><span class="sxs-lookup"><span data-stu-id="f438b-102">AddHandler Statement</span></span>
<span data-ttu-id="f438b-103">Associa um evento com um manipulador de eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f438b-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f438b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f438b-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="f438b-105">Partes</span><span class="sxs-lookup"><span data-stu-id="f438b-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="f438b-106">evento</span><span class="sxs-lookup"><span data-stu-id="f438b-106">event</span></span>|<span data-ttu-id="f438b-107">O nome do evento para manipular.</span><span class="sxs-lookup"><span data-stu-id="f438b-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="f438b-108">O nome de um procedimento que manipula o evento.</span><span class="sxs-lookup"><span data-stu-id="f438b-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="f438b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f438b-109">Remarks</span></span>  
 <span data-ttu-id="f438b-110">O `AddHandler` e `RemoveHandler` instruções permitem que você inicie e pare a manipulação de eventos a qualquer momento durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="f438b-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="f438b-111">A assinatura do `eventhandler` procedimento deve corresponder à assinatura do evento `event`.</span><span class="sxs-lookup"><span data-stu-id="f438b-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="f438b-112">O `Handles` palavra-chave e o `AddHandler` instrução os dois permitem que você especifique que determinados procedimentos manipulem eventos específicos, mas há diferenças.</span><span class="sxs-lookup"><span data-stu-id="f438b-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="f438b-113">O `AddHandler` instrução conecta os procedimentos a eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f438b-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="f438b-114">Use o `Handles` palavra-chave ao definir um procedimento para especificar que ele manipula um evento específico.</span><span class="sxs-lookup"><span data-stu-id="f438b-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="f438b-115">Para obter mais informações, consulte [manipula](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f438b-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f438b-116">Para eventos personalizados, o `AddHandler` instrução invoca o evento `AddHandler` acessador.</span><span class="sxs-lookup"><span data-stu-id="f438b-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="f438b-117">Para obter mais informações sobre eventos personalizados, consulte [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f438b-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f438b-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f438b-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="f438b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f438b-119">See also</span></span>

- [<span data-ttu-id="f438b-120">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="f438b-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="f438b-121">Handles</span><span class="sxs-lookup"><span data-stu-id="f438b-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="f438b-122">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="f438b-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="f438b-123">Eventos</span><span class="sxs-lookup"><span data-stu-id="f438b-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
