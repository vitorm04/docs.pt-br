---
title: "'.' ou '!' à esquerda só podem aparecer dentro de uma instrução 'With'"
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 149acc2baac0f45fa971a11f254d694526d140d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397318"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="a84ee-102">'.' ou '!' à esquerda só podem aparecer dentro de uma instrução 'With'</span><span class="sxs-lookup"><span data-stu-id="a84ee-102">Leading '.' or '!' can only appear inside a 'With' statement</span></span>
<span data-ttu-id="a84ee-103">Um período (.) ou ponto de exclamação (!) que não está dentro de um `With` bloco ocorre sem uma expressão à esquerda.</span><span class="sxs-lookup"><span data-stu-id="a84ee-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="a84ee-104">O acesso de membro ( `.` ) e o acesso de membro de dicionário ( `!` ) exigem uma expressão especificando o elemento que contém o membro.</span><span class="sxs-lookup"><span data-stu-id="a84ee-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="a84ee-105">Isso deve aparecer imediatamente à esquerda do acessador ou como o destino de um `With` bloco que contém o acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="a84ee-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="a84ee-106">**ID do erro:** BC30157</span><span class="sxs-lookup"><span data-stu-id="a84ee-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a84ee-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a84ee-107">To correct this error</span></span>  
  
1. <span data-ttu-id="a84ee-108">Verifique se o `With` bloco está formatado corretamente.</span><span class="sxs-lookup"><span data-stu-id="a84ee-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2. <span data-ttu-id="a84ee-109">Se não houver nenhum `With` bloco, adicione uma expressão à esquerda do acessador que é avaliada como um elemento definido que contém o membro.</span><span class="sxs-lookup"><span data-stu-id="a84ee-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84ee-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="a84ee-110">See also</span></span>

- [<span data-ttu-id="a84ee-111">Caracteres especiais no código</span><span class="sxs-lookup"><span data-stu-id="a84ee-111">Special Characters in Code</span></span>](../../programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="a84ee-112">Instrução With...End With</span><span class="sxs-lookup"><span data-stu-id="a84ee-112">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
