---
title: Instrução RemoveHandler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 3a839a7d05d05066f6c0f774a683c8fc83c19643
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957719"
---
# <a name="removehandler-statement"></a><span data-ttu-id="0d1b2-102">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="0d1b2-102">RemoveHandler Statement</span></span>
<span data-ttu-id="0d1b2-103">Remove a associação entre um evento e um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="0d1b2-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d1b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d1b2-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="0d1b2-105">Partes</span><span class="sxs-lookup"><span data-stu-id="0d1b2-105">Parts</span></span>  
  
|<span data-ttu-id="0d1b2-106">Termo</span><span class="sxs-lookup"><span data-stu-id="0d1b2-106">Term</span></span>|<span data-ttu-id="0d1b2-107">Definição</span><span class="sxs-lookup"><span data-stu-id="0d1b2-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="0d1b2-108">O nome do evento que está sendo manipulado.</span><span class="sxs-lookup"><span data-stu-id="0d1b2-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="0d1b2-109">O nome do procedimento que está manipulando o evento no momento.</span><span class="sxs-lookup"><span data-stu-id="0d1b2-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d1b2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d1b2-110">Remarks</span></span>  
 <span data-ttu-id="0d1b2-111">As `AddHandler` instruções `RemoveHandler` e permitem que você inicie e interrompa a manipulação de eventos para um evento específico a qualquer momento durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="0d1b2-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d1b2-112">Para eventos personalizados, a `RemoveHandler` instrução invoca o acessador `RemoveHandler` do evento.</span><span class="sxs-lookup"><span data-stu-id="0d1b2-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="0d1b2-113">Para obter mais informações sobre eventos personalizados, consulte [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0d1b2-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d1b2-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d1b2-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="0d1b2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d1b2-115">See also</span></span>

- [<span data-ttu-id="0d1b2-116">Instrução AddHandler</span><span class="sxs-lookup"><span data-stu-id="0d1b2-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="0d1b2-117">Handles</span><span class="sxs-lookup"><span data-stu-id="0d1b2-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="0d1b2-118">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="0d1b2-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="0d1b2-119">Eventos</span><span class="sxs-lookup"><span data-stu-id="0d1b2-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
