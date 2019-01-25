---
title: Instrução não é válida dentro de um método / lambda
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: 8002fc347561fd5087aea474b45ef427ee8f8ec9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508078"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="d5541-102">A instrução não é válida dentro de um método/lambda de várias linhas</span><span class="sxs-lookup"><span data-stu-id="d5541-102">Statement is not valid inside a method/multiline lambda</span></span>
<span data-ttu-id="d5541-103">A instrução não é válida dentro de um `Sub`, `Function`, propriedade `Get`, ou a propriedade `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="d5541-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="d5541-104">Algumas instruções podem ser colocadas no nível de módulo ou classe.</span><span class="sxs-lookup"><span data-stu-id="d5541-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="d5541-105">Outros, como `Option Strict`, deve estar no nível de namespace e preceder todas as outras declarações.</span><span class="sxs-lookup"><span data-stu-id="d5541-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="d5541-106">**ID do erro:** BC30024</span><span class="sxs-lookup"><span data-stu-id="d5541-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d5541-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d5541-107">To correct this error</span></span>  
  
-   <span data-ttu-id="d5541-108">Remova a instrução do procedimento.</span><span class="sxs-lookup"><span data-stu-id="d5541-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5541-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5541-109">See also</span></span>
- [<span data-ttu-id="d5541-110">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="d5541-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d5541-111">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="d5541-111">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d5541-112">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="d5541-112">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="d5541-113">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="d5541-113">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
