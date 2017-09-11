---
title: "O modificador &quot;Custom&quot; não é válido em eventos declarados sem tipos delegados explícitos | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
dev_langs:
- VB
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 9
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
ms.openlocfilehash: 449e5a690f06ce35d1ccc799daf5f2c1ad1c6dac
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="f50a7-102">O modificador 'Custom' não é válido em eventos declarados sem tipos delegados explícitos</span><span class="sxs-lookup"><span data-stu-id="f50a7-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="f50a7-103">Diferentemente de um evento não-personalizado, uma `Custom Event` declaração requer um `As` cláusula após o nome do evento que especifica explicitamente o tipo delegado para o evento.</span><span class="sxs-lookup"><span data-stu-id="f50a7-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="f50a7-104">Os eventos não-personalizados podem ser definidos com um `As` cláusula e explícito tipo delegado, ou com um parâmetro de lista imediatamente após o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="f50a7-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="f50a7-105">**ID do erro:** BC31122</span><span class="sxs-lookup"><span data-stu-id="f50a7-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f50a7-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f50a7-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="f50a7-107">Defina um delegado com a mesma lista de parâmetros que o evento personalizado.</span><span class="sxs-lookup"><span data-stu-id="f50a7-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="f50a7-108">Por exemplo, se o `Custom Event` foi definido pela `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, então o delegado correspondente viria a seguir.</span><span class="sxs-lookup"><span data-stu-id="f50a7-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     <span data-ttu-id="f50a7-109">[!code-vb[VbVbalrEventError n º&18;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f50a7-109">[!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]</span></span>  
  
2.  <span data-ttu-id="f50a7-110">Substitua a lista de parâmetros do evento personalizado com um `As` cláusula especificando o tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="f50a7-110">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="f50a7-111">Continuando com o exemplo `Custom Event` declaração poderia ser reescrita da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="f50a7-111">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     <span data-ttu-id="f50a7-112">[!code-vb[19 VbVbalrEventError](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f50a7-112">[!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f50a7-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f50a7-113">Example</span></span>  
 <span data-ttu-id="f50a7-114">Este exemplo declara um `Custom Event` e especifica a necessário `As` cláusula com um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="f50a7-114">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 <span data-ttu-id="f50a7-115">[!code-vb[VbVbalrEventError n º&2;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f50a7-115">[!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f50a7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f50a7-116">See Also</span></span>  
 <span data-ttu-id="f50a7-117">[Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f50a7-117">[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="f50a7-118"> [Instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f50a7-118"> [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="f50a7-119"> [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="f50a7-119"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
