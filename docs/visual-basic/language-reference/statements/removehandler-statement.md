---
title: "Instrução RemoveHandler | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
dev_langs:
- VB
helpviewer_keywords:
- RemoveHandler keyword
- RemoveHandler statement
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: 14
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
ms.openlocfilehash: 6e614a1dce4894dcd18509854f3cae149665cbf0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="removehandler-statement"></a><span data-ttu-id="0abc7-102">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="0abc7-102">RemoveHandler Statement</span></span>
<span data-ttu-id="0abc7-103">Remove a associação entre um evento e um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="0abc7-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0abc7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0abc7-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="0abc7-105">Partes</span><span class="sxs-lookup"><span data-stu-id="0abc7-105">Parts</span></span>  
  
|<span data-ttu-id="0abc7-106">Termo</span><span class="sxs-lookup"><span data-stu-id="0abc7-106">Term</span></span>|<span data-ttu-id="0abc7-107">Definição</span><span class="sxs-lookup"><span data-stu-id="0abc7-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="0abc7-108">O nome do evento que está sendo manipulado.</span><span class="sxs-lookup"><span data-stu-id="0abc7-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="0abc7-109">O nome do procedimento atualmente manipulando o evento.</span><span class="sxs-lookup"><span data-stu-id="0abc7-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0abc7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0abc7-110">Remarks</span></span>  
 <span data-ttu-id="0abc7-111">O `AddHandler` e `RemoveHandler` instruções permitem que você inicie e pare a manipulação de eventos para um evento específico a qualquer momento durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="0abc7-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0abc7-112">Para eventos personalizados, o `RemoveHandler` instrução chama o evento `RemoveHandler` acessador.</span><span class="sxs-lookup"><span data-stu-id="0abc7-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="0abc7-113">Para obter mais informações sobre eventos personalizados, consulte [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0abc7-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0abc7-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0abc7-114">Example</span></span>  
 <span data-ttu-id="0abc7-115">[!code-vb[17 VbVbalrEvents](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0abc7-115">[!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0abc7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0abc7-116">See Also</span></span>  
 <span data-ttu-id="0abc7-117">[Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0abc7-117">[AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span></span>  
<span data-ttu-id="0abc7-118"> [Identificadores](../../../visual-basic/language-reference/statements/handles-clause.md) </span><span class="sxs-lookup"><span data-stu-id="0abc7-118"> [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) </span></span>  
<span data-ttu-id="0abc7-119"> [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0abc7-119"> [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="0abc7-120"> [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="0abc7-120"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
