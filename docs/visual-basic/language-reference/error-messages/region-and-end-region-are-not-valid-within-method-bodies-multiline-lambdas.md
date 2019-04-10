---
title: "Instruções '#Region' e ' #End' não são válidas dentro de corpos / lambdas de método"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c41b95da7e3565ae7aaf332fe49361336e79f7c7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303902"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="70cee-102">As instruções '#Region' e '#End Region' não são válidas dentro dos corpos/lambdas de várias linhas do método</span><span class="sxs-lookup"><span data-stu-id="70cee-102">'#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="70cee-103">O `#Region` bloco deve ser declarado em um nível de classe, módulo ou namespace.</span><span class="sxs-lookup"><span data-stu-id="70cee-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="70cee-104">Uma região recolhível pode incluir um ou mais procedimentos, mas ele não pode começar ou terminar dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="70cee-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="70cee-105">**ID do erro:** BC32025</span><span class="sxs-lookup"><span data-stu-id="70cee-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70cee-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="70cee-106">To correct this error</span></span>  
  
1. <span data-ttu-id="70cee-107">Certifique-se de que o procedimento anterior é encerrado corretamente com um `End Function` ou `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="70cee-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="70cee-108">Certifique-se de que o `#Region` e `#End Region` diretivas estão no mesmo bloco de código.</span><span class="sxs-lookup"><span data-stu-id="70cee-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70cee-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70cee-109">See also</span></span>

- [<span data-ttu-id="70cee-110">Diretiva #Region</span><span class="sxs-lookup"><span data-stu-id="70cee-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
