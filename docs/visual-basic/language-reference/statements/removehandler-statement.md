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
ms.openlocfilehash: 47f35bd76d7734878e7b5b206b4aecd856276593
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582018"
---
# <a name="removehandler-statement"></a><span data-ttu-id="ce2b0-102">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="ce2b0-102">RemoveHandler Statement</span></span>
<span data-ttu-id="ce2b0-103">Remove a associação entre um evento e um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="ce2b0-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce2b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce2b0-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="ce2b0-105">Partes</span><span class="sxs-lookup"><span data-stu-id="ce2b0-105">Parts</span></span>  
  
|<span data-ttu-id="ce2b0-106">Termo</span><span class="sxs-lookup"><span data-stu-id="ce2b0-106">Term</span></span>|<span data-ttu-id="ce2b0-107">Definição</span><span class="sxs-lookup"><span data-stu-id="ce2b0-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="ce2b0-108">O nome do evento que está sendo manipulado.</span><span class="sxs-lookup"><span data-stu-id="ce2b0-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="ce2b0-109">O nome do procedimento que está manipulando o evento no momento.</span><span class="sxs-lookup"><span data-stu-id="ce2b0-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce2b0-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ce2b0-110">Remarks</span></span>  
 <span data-ttu-id="ce2b0-111">As instruções `AddHandler` e `RemoveHandler` permitem iniciar e parar a manipulação de eventos para um evento específico a qualquer momento durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="ce2b0-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce2b0-112">Para eventos personalizados, a instrução `RemoveHandler` invoca o acessador de `RemoveHandler` do evento.</span><span class="sxs-lookup"><span data-stu-id="ce2b0-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="ce2b0-113">Para obter mais informações sobre eventos personalizados, consulte [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ce2b0-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce2b0-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ce2b0-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="ce2b0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce2b0-115">See also</span></span>

- [<span data-ttu-id="ce2b0-116">Instrução AddHandler</span><span class="sxs-lookup"><span data-stu-id="ce2b0-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="ce2b0-117">Handles</span><span class="sxs-lookup"><span data-stu-id="ce2b0-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="ce2b0-118">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="ce2b0-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="ce2b0-119">Eventos</span><span class="sxs-lookup"><span data-stu-id="ce2b0-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
