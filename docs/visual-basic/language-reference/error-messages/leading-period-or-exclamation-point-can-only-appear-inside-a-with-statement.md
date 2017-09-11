---
title: "À esquerda &quot;. &quot;ou&quot;!&quot; só pode aparecer dentro de uma instrução &quot;With&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30157
- bc30157
dev_langs:
- VB
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: 10
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
ms.openlocfilehash: 6f45d5fbf872cf18ea2f3ec6f5fef552f7bdeb0c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a><span data-ttu-id="0f6f1-102">À esquerda '. 'ou'!' só pode aparecer dentro de uma instrução 'With'</span><span class="sxs-lookup"><span data-stu-id="0f6f1-102">Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement</span></span>
<span data-ttu-id="0f6f1-103">Um ponto (.) ou ponto de exclamação (!) que não está dentro um `With` bloco ocorre sem uma expressão à esquerda.</span><span class="sxs-lookup"><span data-stu-id="0f6f1-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="0f6f1-104">Acesso de membro (`.`) e acesso de membro de dicionário (`!`) requerem uma expressão especificando o elemento que contém o membro.</span><span class="sxs-lookup"><span data-stu-id="0f6f1-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="0f6f1-105">Isso deve aparecer imediatamente à esquerda do acessador ou como o destino de uma `With` bloco que contém o acesso do membro.</span><span class="sxs-lookup"><span data-stu-id="0f6f1-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="0f6f1-106">**ID do erro:** BC30157</span><span class="sxs-lookup"><span data-stu-id="0f6f1-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f6f1-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0f6f1-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="0f6f1-108">Verifique se o `With` bloco está formatado corretamente.</span><span class="sxs-lookup"><span data-stu-id="0f6f1-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2.  <span data-ttu-id="0f6f1-109">Se não houver nenhum `With` bloco, adicione uma expressão à esquerda do acessador que avalia para um elemento definido que contém o membro.</span><span class="sxs-lookup"><span data-stu-id="0f6f1-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f6f1-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f6f1-110">See Also</span></span>  
 <span data-ttu-id="0f6f1-111">[Caracteres especiais no código](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md) </span><span class="sxs-lookup"><span data-stu-id="0f6f1-111">[Special Characters in Code](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md) </span></span>  
<span data-ttu-id="0f6f1-112"> [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="0f6f1-112"> [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span></span>
