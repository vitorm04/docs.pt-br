---
title: A instrução não pode finalizar um bloco fora de uma linha &#39; se &#39; instrução
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73fe3eb44e904366db7d505bbe8c5fef461eb78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="d0051-102">A instrução não pode finalizar um bloco fora de uma linha &#39; se &#39; instrução</span><span class="sxs-lookup"><span data-stu-id="d0051-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="d0051-103">Uma única linha `If` instrução contém várias instruções, separadas por dois-pontos (:), um dos quais é um `End` instrução para um bloco de controle fora de linha única `If`.</span><span class="sxs-lookup"><span data-stu-id="d0051-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="d0051-104">Linha `If` instruções não usa o `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="d0051-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="d0051-105">**ID do erro:** BC32005</span><span class="sxs-lookup"><span data-stu-id="d0051-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d0051-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d0051-106">To correct this error</span></span>  
  
-   <span data-ttu-id="d0051-107">Mover a linha `If` instrução fora do bloco de controle que contém o `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="d0051-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0051-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0051-108">See Also</span></span>  
 [<span data-ttu-id="d0051-109">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="d0051-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
