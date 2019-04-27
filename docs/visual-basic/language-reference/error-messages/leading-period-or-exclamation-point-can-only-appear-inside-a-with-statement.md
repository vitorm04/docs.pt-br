---
title: "'.' ou '!' à esquerda só podem aparecer dentro de uma instrução 'With'"
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 15390fb506fe9bca10f6917f5b26451a5569bece
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921115"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="c3a2f-102">'.' ou '!' à esquerda só podem aparecer dentro de uma instrução 'With'</span><span class="sxs-lookup"><span data-stu-id="c3a2f-102">Leading '.' or '!' can only appear inside a 'With' statement</span></span>
<span data-ttu-id="c3a2f-103">Um ponto (.) ou um ponto de exclamação (!) que não está dentro um `With` bloco ocorre sem uma expressão à esquerda.</span><span class="sxs-lookup"><span data-stu-id="c3a2f-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="c3a2f-104">Acesso de membro (`.`) e acesso de membro de dicionário (`!`) exigem uma expressão que especifica o elemento que contém o membro.</span><span class="sxs-lookup"><span data-stu-id="c3a2f-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="c3a2f-105">Isso deve aparecer imediatamente à esquerda do acessador ou como o destino de um `With` bloco que contém o acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="c3a2f-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="c3a2f-106">**ID do erro:** BC30157</span><span class="sxs-lookup"><span data-stu-id="c3a2f-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c3a2f-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c3a2f-107">To correct this error</span></span>  
  
1. <span data-ttu-id="c3a2f-108">Certifique-se de que o `With` bloco está formatado corretamente.</span><span class="sxs-lookup"><span data-stu-id="c3a2f-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2. <span data-ttu-id="c3a2f-109">Se não houver nenhum `With` de blocos, adicione uma expressão à esquerda do acessador que é avaliada para um elemento definido que contém o membro.</span><span class="sxs-lookup"><span data-stu-id="c3a2f-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a2f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3a2f-110">See also</span></span>

- [<span data-ttu-id="c3a2f-111">Caracteres Especiais no Código</span><span class="sxs-lookup"><span data-stu-id="c3a2f-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="c3a2f-112">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="c3a2f-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
