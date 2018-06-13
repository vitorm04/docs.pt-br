---
title: A instrução não pode finalizar um bloco fora de uma linha &#39;se&#39; instrução
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: af3006ddc35dfcaa52a54229881baa48cfb7809a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596678"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="f0255-102">A instrução não pode finalizar um bloco fora de uma linha &#39;se&#39; instrução</span><span class="sxs-lookup"><span data-stu-id="f0255-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="f0255-103">Uma única linha `If` instrução contém várias instruções, separadas por dois-pontos (:), um dos quais é um `End` instrução para um bloco de controle fora de linha única `If`.</span><span class="sxs-lookup"><span data-stu-id="f0255-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="f0255-104">Linha `If` instruções não usa o `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="f0255-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="f0255-105">**ID do erro:** BC32005</span><span class="sxs-lookup"><span data-stu-id="f0255-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f0255-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f0255-106">To correct this error</span></span>  
  
-   <span data-ttu-id="f0255-107">Mover a linha `If` instrução fora do bloco de controle que contém o `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="f0255-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0255-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0255-108">See Also</span></span>  
 [<span data-ttu-id="f0255-109">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="f0255-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
