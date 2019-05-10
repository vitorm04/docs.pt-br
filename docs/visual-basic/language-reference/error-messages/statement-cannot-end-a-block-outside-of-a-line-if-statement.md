---
title: A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 0e645ccf17d0aba702a576791622aa4e9b3dd5e0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593262"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="bfb3c-102">A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha</span><span class="sxs-lookup"><span data-stu-id="bfb3c-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="bfb3c-103">Uma linha única `If` instrução contém várias instruções separadas por dois-pontos (:), um dos quais é um `End` instrução para um bloco de controle fora de linha única `If`.</span><span class="sxs-lookup"><span data-stu-id="bfb3c-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="bfb3c-104">Linha única `If` instruções não usam o `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="bfb3c-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="bfb3c-105">**ID do erro:** BC32005</span><span class="sxs-lookup"><span data-stu-id="bfb3c-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bfb3c-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="bfb3c-106">To correct this error</span></span>  
  
- <span data-ttu-id="bfb3c-107">Mover a linha única `If` instrução fora do bloco de controle que contém o `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="bfb3c-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb3c-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfb3c-108">See also</span></span>

- [<span data-ttu-id="bfb3c-109">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="bfb3c-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
