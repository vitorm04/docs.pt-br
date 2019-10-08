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
ms.openlocfilehash: 95277f532488b0cf56114e5ee94dc3528e3a2e02
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004535"
---
# <a name="addhandler-statement"></a><span data-ttu-id="5c53e-102">Instrução AddHandler</span><span class="sxs-lookup"><span data-stu-id="5c53e-102">AddHandler Statement</span></span>
<span data-ttu-id="5c53e-103">Associa um evento a um manipulador de eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5c53e-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c53e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c53e-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="5c53e-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5c53e-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="5c53e-106">evento</span><span class="sxs-lookup"><span data-stu-id="5c53e-106">event</span></span>|<span data-ttu-id="5c53e-107">O nome do evento a ser manipulado.</span><span class="sxs-lookup"><span data-stu-id="5c53e-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="5c53e-108">O nome de um procedimento que manipula o evento.</span><span class="sxs-lookup"><span data-stu-id="5c53e-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="5c53e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c53e-109">Remarks</span></span>  
 <span data-ttu-id="5c53e-110">As instruções `AddHandler` e `RemoveHandler` permitem iniciar e parar a manipulação de eventos a qualquer momento durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="5c53e-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="5c53e-111">A assinatura do procedimento `eventhandler` deve corresponder à assinatura do evento `event`.</span><span class="sxs-lookup"><span data-stu-id="5c53e-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="5c53e-112">A palavra-chave `Handles` e a instrução `AddHandler` permitem que você especifique que procedimentos específicos manipulam eventos específicos, mas há diferenças.</span><span class="sxs-lookup"><span data-stu-id="5c53e-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="5c53e-113">A instrução `AddHandler` conecta procedimentos a eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5c53e-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="5c53e-114">Use a palavra-chave `Handles` ao definir um procedimento para especificar que ele trata de um evento específico.</span><span class="sxs-lookup"><span data-stu-id="5c53e-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="5c53e-115">Para obter mais informações, consulte [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5c53e-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c53e-116">Para eventos personalizados, a instrução `AddHandler` invoca o acessador do evento `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="5c53e-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="5c53e-117">Para obter mais informações sobre eventos personalizados, consulte [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5c53e-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c53e-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c53e-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="5c53e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c53e-119">See also</span></span>

- [<span data-ttu-id="5c53e-120">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="5c53e-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="5c53e-121">Handles</span><span class="sxs-lookup"><span data-stu-id="5c53e-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="5c53e-122">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="5c53e-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="5c53e-123">Eventos</span><span class="sxs-lookup"><span data-stu-id="5c53e-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
