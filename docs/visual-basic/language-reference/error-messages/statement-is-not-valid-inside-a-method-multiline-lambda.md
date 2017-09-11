---
title: "Instrução não é válida dentro de um lambda de várias linhas do método | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30024
- bc30024
dev_langs:
- VB
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
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
ms.openlocfilehash: 8ae1ffd65639f56e7707b880750ae870698aff93
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="e78c3-102">A instrução não é válida dentro de um método/lambda de várias linhas</span><span class="sxs-lookup"><span data-stu-id="e78c3-102">Statement is not valid inside a method/multiline lambda</span></span>
<span data-ttu-id="e78c3-103">A instrução não é válida dentro de um `Sub`, `Function`, propriedade `Get`, ou a propriedade `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="e78c3-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="e78c3-104">Algumas declarações podem ser colocadas no nível de classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="e78c3-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="e78c3-105">Outros, como `Option Strict`, deve estar no nível de namespace e preceder todas as outras declarações.</span><span class="sxs-lookup"><span data-stu-id="e78c3-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="e78c3-106">**ID do erro:** BC30024</span><span class="sxs-lookup"><span data-stu-id="e78c3-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e78c3-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e78c3-107">To correct this error</span></span>  
  
-   <span data-ttu-id="e78c3-108">Remova a declaração do procedimento.</span><span class="sxs-lookup"><span data-stu-id="e78c3-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e78c3-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e78c3-109">See Also</span></span>  
 <span data-ttu-id="e78c3-110">[Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e78c3-110">[Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="e78c3-111"> [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e78c3-111"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="e78c3-112"> [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e78c3-112"> [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) </span></span>  
<span data-ttu-id="e78c3-113"> [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)</span><span class="sxs-lookup"><span data-stu-id="e78c3-113"> [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)</span></span>
