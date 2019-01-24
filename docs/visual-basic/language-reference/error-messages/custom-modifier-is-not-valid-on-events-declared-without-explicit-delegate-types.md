---
title: '&#39;Personalizado&#39; modificador não é válido em eventos declarados sem tipos delegados explícitos'
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: c909973ef1c00cb01179b0e5527dfecd6f41e577
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574775"
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="112db-102">&#39;Personalizado&#39; modificador não é válido em eventos declarados sem tipos delegados explícitos</span><span class="sxs-lookup"><span data-stu-id="112db-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="112db-103">Ao contrário de um evento não-personalizado, uma `Custom Event` declaração requer um `As` cláusula após o nome do evento que especifica explicitamente o tipo de delegado para o evento.</span><span class="sxs-lookup"><span data-stu-id="112db-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="112db-104">Os eventos não-personalizados podem ser definidos com um `As` cláusula e explícito tipo delegado, ou com um parâmetro de lista imediatamente após o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="112db-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="112db-105">**ID do erro:** BC31122</span><span class="sxs-lookup"><span data-stu-id="112db-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="112db-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="112db-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="112db-107">Defina um delegado com a mesma lista de parâmetros que o evento personalizado.</span><span class="sxs-lookup"><span data-stu-id="112db-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="112db-108">Por exemplo, se o `Custom Event` foi definido por `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, em seguida, o delegado correspondente seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="112db-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  <span data-ttu-id="112db-109">Substitua a lista de parâmetros do evento personalizado com um `As` cláusula especificando o tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="112db-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="112db-110">Continuando com o exemplo `Custom Event` declaração poderia ser reescrita da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="112db-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="112db-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="112db-111">Example</span></span>  
 <span data-ttu-id="112db-112">Este exemplo declara uma `Custom Event` e especifica o necessária `As` cláusula com um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="112db-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="112db-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="112db-113">See also</span></span>
- [<span data-ttu-id="112db-114">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="112db-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="112db-115">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="112db-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="112db-116">Eventos</span><span class="sxs-lookup"><span data-stu-id="112db-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
