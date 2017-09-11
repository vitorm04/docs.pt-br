---
title: "A instrução não pode finalizar um bloco fora de uma instrução &quot;If&quot; de linha | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
dev_langs:
- VB
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: 8
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
ms.openlocfilehash: d604791c404e65f3a958485468f62a1de21a18d7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="9c0cb-102">A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha</span><span class="sxs-lookup"><span data-stu-id="9c0cb-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="9c0cb-103">Uma única linha `If` instrução contém várias instruções separadas por dois-pontos (:), um dos quais é um `End` instrução para um bloco de controle de fora a linha `If`.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="9c0cb-104">Linha `If` instruções não use o `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="9c0cb-105">**ID do erro:** BC32005</span><span class="sxs-lookup"><span data-stu-id="9c0cb-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c0cb-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9c0cb-106">To correct this error</span></span>  
  
-   <span data-ttu-id="9c0cb-107">Mover a linha `If` instrução fora do bloco de controle que contém o `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0cb-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c0cb-108">See Also</span></span>  
 [<span data-ttu-id="9c0cb-109">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="9c0cb-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
