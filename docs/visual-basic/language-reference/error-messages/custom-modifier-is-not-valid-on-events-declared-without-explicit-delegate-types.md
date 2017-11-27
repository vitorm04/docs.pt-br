---
title: "&#39; Personalizar &#39; o modificador ' não é válido em eventos declarados sem tipos delegados explícitos"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords: BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 844bd033ea05e373b04a04f80777af77179c1263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="6d20a-102">&#39; Personalizar &#39; o modificador ' não é válido em eventos declarados sem tipos delegados explícitos</span><span class="sxs-lookup"><span data-stu-id="6d20a-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="6d20a-103">Diferentemente de um evento não-personalizado, uma `Custom Event` declaração requer um `As` cláusula após o nome do evento que especifica explicitamente o tipo delegado do evento.</span><span class="sxs-lookup"><span data-stu-id="6d20a-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="6d20a-104">Eventos personalizados não podem ser definidos com um `As` cláusula explícita tipo delegate e com um parâmetro de lista imediatamente após o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="6d20a-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="6d20a-105">**ID do erro:** BC31122</span><span class="sxs-lookup"><span data-stu-id="6d20a-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6d20a-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6d20a-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="6d20a-107">Defina um delegado com a mesma lista de parâmetros que o evento personalizado.</span><span class="sxs-lookup"><span data-stu-id="6d20a-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="6d20a-108">Por exemplo, se o `Custom Event` foi definido por `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, em seguida, o delegado correspondente seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="6d20a-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  <span data-ttu-id="6d20a-109">Substituir a lista de parâmetros do evento personalizado com um `As` cláusula especificando o tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="6d20a-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="6d20a-110">Continuando com o exemplo `Custom Event` declaração poderia ser reescrita da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="6d20a-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="6d20a-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d20a-111">Example</span></span>  
 <span data-ttu-id="6d20a-112">Este exemplo declara um `Custom Event` e especifica necessários `As` cláusula com um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="6d20a-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6d20a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d20a-113">See Also</span></span>  
 [<span data-ttu-id="6d20a-114">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="6d20a-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="6d20a-115">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="6d20a-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="6d20a-116">Eventos</span><span class="sxs-lookup"><span data-stu-id="6d20a-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
