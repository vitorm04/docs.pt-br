---
title: Instrução 'Class' deve finalizar com 'End Class' correspondente
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 6889e97aad913f6911ce438892752542de0d10f0
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163188"
---
# <a name="bc30481-class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="db0b5-102">BC30481: a instrução ' class ' deve terminar com uma ' End Class ' correspondente</span><span class="sxs-lookup"><span data-stu-id="db0b5-102">BC30481: 'Class' statement must end with a matching 'End Class'</span></span>

<span data-ttu-id="db0b5-103">`Class` é usado para iniciar um `Class` bloco; portanto, ele só pode aparecer no início do bloco, com uma instrução correspondente que `End Class` termina o bloco.</span><span class="sxs-lookup"><span data-stu-id="db0b5-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="db0b5-104">Você tem uma instrução redundante `Class` ou não terminou seu `Class` bloco com `End Class` .</span><span class="sxs-lookup"><span data-stu-id="db0b5-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>

 <span data-ttu-id="db0b5-105">**ID do erro:** BC30481</span><span class="sxs-lookup"><span data-stu-id="db0b5-105">**Error ID:** BC30481</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="db0b5-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="db0b5-106">To correct this error</span></span>

- <span data-ttu-id="db0b5-107">Localize e remova a instrução desnecessária `Class` .</span><span class="sxs-lookup"><span data-stu-id="db0b5-107">Locate and remove the unnecessary `Class` statement.</span></span>

- <span data-ttu-id="db0b5-108">Conclua o `Class` bloco com uma correspondência `End Class` .</span><span class="sxs-lookup"><span data-stu-id="db0b5-108">Conclude the `Class` block with a matching `End Class`.</span></span>

## <a name="see-also"></a><span data-ttu-id="db0b5-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="db0b5-109">See also</span></span>

- [<span data-ttu-id="db0b5-110">\<keyword>Instrução End</span><span class="sxs-lookup"><span data-stu-id="db0b5-110">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="db0b5-111">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="db0b5-111">Class Statement</span></span>](../statements/class-statement.md)
