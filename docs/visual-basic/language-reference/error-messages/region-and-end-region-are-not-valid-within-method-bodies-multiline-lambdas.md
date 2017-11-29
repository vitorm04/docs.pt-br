---
title: "&#39; #Region &#39; e &#39; região #End &#39; instruções não são válidas em lambdas de várias linhas do corpo de método"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords: BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 614d0c7324bfbf07bc5736c799e8b54937ead081
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="35f25-102">&#39; #Region &#39; e &#39; região #End &#39; instruções não são válidas dentro do método corpos/lambdas multilinha</span><span class="sxs-lookup"><span data-stu-id="35f25-102">&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="35f25-103">O `#Region` bloco deve ser declarado em um nível de namespace, módulo ou classe.</span><span class="sxs-lookup"><span data-stu-id="35f25-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="35f25-104">Uma região recolhível pode incluir um ou mais procedimentos, mas ele não pode começar ou terminar dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="35f25-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="35f25-105">**ID do erro:** BC32025</span><span class="sxs-lookup"><span data-stu-id="35f25-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="35f25-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="35f25-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="35f25-107">Certifique-se de que o procedimento anterior é encerrado corretamente com um `End Function` ou `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="35f25-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="35f25-108">Certifique-se de que o `#Region` e `#End Region` diretivas estão no mesmo bloco de código.</span><span class="sxs-lookup"><span data-stu-id="35f25-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f25-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35f25-109">See Also</span></span>  
 [<span data-ttu-id="35f25-110">Diretiva #Region</span><span class="sxs-lookup"><span data-stu-id="35f25-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
