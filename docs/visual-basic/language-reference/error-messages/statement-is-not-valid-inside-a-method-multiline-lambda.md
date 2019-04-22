---
title: Instrução não é válida dentro de um método / lambda
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: 994cafc44a37d16d0f70caec560f530c6a836ec0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841557"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="31b58-102">A instrução não é válida dentro de um método/lambda de várias linhas</span><span class="sxs-lookup"><span data-stu-id="31b58-102">Statement is not valid inside a method/multiline lambda</span></span>
<span data-ttu-id="31b58-103">A instrução não é válida dentro de um `Sub`, `Function`, propriedade `Get`, ou a propriedade `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="31b58-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="31b58-104">Algumas instruções podem ser colocadas no nível de módulo ou classe.</span><span class="sxs-lookup"><span data-stu-id="31b58-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="31b58-105">Outros, como `Option Strict`, deve estar no nível de namespace e preceder todas as outras declarações.</span><span class="sxs-lookup"><span data-stu-id="31b58-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="31b58-106">**ID do erro:** BC30024</span><span class="sxs-lookup"><span data-stu-id="31b58-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="31b58-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="31b58-107">To correct this error</span></span>  
  
-   <span data-ttu-id="31b58-108">Remova a instrução do procedimento.</span><span class="sxs-lookup"><span data-stu-id="31b58-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b58-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31b58-109">See also</span></span>

- [<span data-ttu-id="31b58-110">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="31b58-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="31b58-111">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="31b58-111">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="31b58-112">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="31b58-112">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="31b58-113">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="31b58-113">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
