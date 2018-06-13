---
title: Instrução RemoveHandler
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 0d982768707948bd6c616445509e16a462b86f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597982"
---
# <a name="removehandler-statement"></a><span data-ttu-id="a2042-102">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="a2042-102">RemoveHandler Statement</span></span>
<span data-ttu-id="a2042-103">Remove a associação entre um evento e um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="a2042-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2042-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2042-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="a2042-105">Partes</span><span class="sxs-lookup"><span data-stu-id="a2042-105">Parts</span></span>  
  
|<span data-ttu-id="a2042-106">Termo</span><span class="sxs-lookup"><span data-stu-id="a2042-106">Term</span></span>|<span data-ttu-id="a2042-107">Definição</span><span class="sxs-lookup"><span data-stu-id="a2042-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="a2042-108">O nome do evento que está sendo tratado.</span><span class="sxs-lookup"><span data-stu-id="a2042-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="a2042-109">O nome do procedimento atualmente manipular o evento.</span><span class="sxs-lookup"><span data-stu-id="a2042-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2042-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2042-110">Remarks</span></span>  
 <span data-ttu-id="a2042-111">O `AddHandler` e `RemoveHandler` instruções permitem iniciar e interromper a manipulação de eventos para um evento específico a qualquer momento durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="a2042-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2042-112">Para eventos personalizados, o `RemoveHandler` instrução invoca o evento `RemoveHandler` acessador.</span><span class="sxs-lookup"><span data-stu-id="a2042-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="a2042-113">Para obter mais informações sobre eventos personalizados, consulte [instrução Event](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a2042-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2042-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2042-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a2042-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2042-115">See Also</span></span>  
 [<span data-ttu-id="a2042-116">Instrução AddHandler</span><span class="sxs-lookup"><span data-stu-id="a2042-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="a2042-117">Handles</span><span class="sxs-lookup"><span data-stu-id="a2042-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="a2042-118">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="a2042-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="a2042-119">Eventos</span><span class="sxs-lookup"><span data-stu-id="a2042-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
