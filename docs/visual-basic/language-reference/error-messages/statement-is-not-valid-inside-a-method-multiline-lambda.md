---
title: A instrução não é válida dentro de um método/lambda de várias linhas
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: d5d756f1772b9519613e163119b88a3057d36cf3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870624"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="be0af-102">A instrução não é válida dentro de um método/lambda de várias linhas</span><span class="sxs-lookup"><span data-stu-id="be0af-102">Statement is not valid inside a method/multiline lambda</span></span>

<span data-ttu-id="be0af-103">A instrução não é válida dentro de `Sub` um `Function` procedimento,, propriedade `Get` ou propriedade `Set` .</span><span class="sxs-lookup"><span data-stu-id="be0af-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="be0af-104">Algumas instruções podem ser colocadas no nível do módulo ou da classe.</span><span class="sxs-lookup"><span data-stu-id="be0af-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="be0af-105">Outros, como `Option Strict` , devem estar no nível de namespace e preceder todas as outras declarações.</span><span class="sxs-lookup"><span data-stu-id="be0af-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="be0af-106">**ID do erro:** BC30024</span><span class="sxs-lookup"><span data-stu-id="be0af-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="be0af-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="be0af-107">To correct this error</span></span>  
  
- <span data-ttu-id="be0af-108">Remova a instrução do procedimento.</span><span class="sxs-lookup"><span data-stu-id="be0af-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be0af-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="be0af-109">See also</span></span>

- [<span data-ttu-id="be0af-110">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="be0af-110">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="be0af-111">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="be0af-111">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="be0af-112">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="be0af-112">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="be0af-113">Instrução SET</span><span class="sxs-lookup"><span data-stu-id="be0af-113">Set Statement</span></span>](../statements/set-statement.md)
