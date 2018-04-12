---
title: À esquerda &#39;. &#39; ou &#39;! &#39; só pode aparecer dentro de um &#39; Com &#39; instrução
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 961f2d737123ab68b200d5fc7658cb81291a5de6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a><span data-ttu-id="4d72e-102">À esquerda &#39;. &#39; ou &#39;! &#39; só pode aparecer dentro de um &#39; Com &#39; instrução</span><span class="sxs-lookup"><span data-stu-id="4d72e-102">Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement</span></span>
<span data-ttu-id="4d72e-103">Um ponto (.) ou um ponto de exclamação (!) que não está dentro um `With` bloco ocorre sem uma expressão à esquerda.</span><span class="sxs-lookup"><span data-stu-id="4d72e-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="4d72e-104">Acesso de membro (`.`) e acesso de membro de dicionário (`!`) exigem uma expressão que especifica o elemento que contém o membro.</span><span class="sxs-lookup"><span data-stu-id="4d72e-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="4d72e-105">Isso deve aparecer imediatamente à esquerda do acessador ou como o destino de um `With` bloco que contém o acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="4d72e-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="4d72e-106">**ID do erro:** BC30157</span><span class="sxs-lookup"><span data-stu-id="4d72e-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d72e-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4d72e-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="4d72e-108">Certifique-se de que o `With` bloco está formatado corretamente.</span><span class="sxs-lookup"><span data-stu-id="4d72e-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2.  <span data-ttu-id="4d72e-109">Se não houver nenhum `With` bloco, adicione uma expressão à esquerda do acessador que avalia para um elemento definido que contém o membro.</span><span class="sxs-lookup"><span data-stu-id="4d72e-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d72e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d72e-110">See Also</span></span>  
 [<span data-ttu-id="4d72e-111">Caracteres Especiais no Código</span><span class="sxs-lookup"><span data-stu-id="4d72e-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [<span data-ttu-id="4d72e-112">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="4d72e-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
