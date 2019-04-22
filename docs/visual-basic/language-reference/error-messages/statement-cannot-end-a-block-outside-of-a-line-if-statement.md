---
title: A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 85573099ec0a3f8a23c17bdf384c4c105f9157df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825780"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="5e55b-102">A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha</span><span class="sxs-lookup"><span data-stu-id="5e55b-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="5e55b-103">Uma linha única `If` instrução contém várias instruções separadas por dois-pontos (:), um dos quais é um `End` instrução para um bloco de controle fora de linha única `If`.</span><span class="sxs-lookup"><span data-stu-id="5e55b-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="5e55b-104">Linha única `If` instruções não usam o `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="5e55b-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="5e55b-105">**ID do erro:** BC32005</span><span class="sxs-lookup"><span data-stu-id="5e55b-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5e55b-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5e55b-106">To correct this error</span></span>  
  
-   <span data-ttu-id="5e55b-107">Mover a linha única `If` instrução fora do bloco de controle que contém o `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="5e55b-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e55b-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e55b-108">See also</span></span>

- [<span data-ttu-id="5e55b-109">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="5e55b-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
