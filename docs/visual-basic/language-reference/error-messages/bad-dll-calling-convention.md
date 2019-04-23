---
title: Convenção de chamada de DLL inválida
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: f7b0c3a6edbe0b950195306fa66287ff9b209bfe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306612"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="14dce-102">Convenção de chamada de DLL inválida</span><span class="sxs-lookup"><span data-stu-id="14dce-102">Bad DLL calling convention</span></span>
<span data-ttu-id="14dce-103">Argumentos passados para uma biblioteca de vínculo dinâmico (DLL) devem corresponder exatamente aos esperados pela rotina.</span><span class="sxs-lookup"><span data-stu-id="14dce-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="14dce-104">Convenções de chamada lidam com o número, tipo e ordem dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="14dce-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="14dce-105">Seu programa pode chamar uma rotina em uma DLL que está sendo passada a um tipo incorreto ou o número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="14dce-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="14dce-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="14dce-106">To correct this error</span></span>  
  
1. <span data-ttu-id="14dce-107">Verifique se que todos os tipos de argumento de acordo com aquelas especificadas na declaração da rotina que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="14dce-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="14dce-108">Verifique se que você estiver passando o mesmo número de argumentos indicado na declaração da rotina que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="14dce-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="14dce-109">Se a rotina DLL espera argumentos por valor, certifique-se `ByVal` é especificado para esses argumentos na declaração para a rotina.</span><span class="sxs-lookup"><span data-stu-id="14dce-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14dce-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14dce-110">See also</span></span>

- [<span data-ttu-id="14dce-111">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="14dce-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="14dce-112">Instrução Call</span><span class="sxs-lookup"><span data-stu-id="14dce-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)
- [<span data-ttu-id="14dce-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="14dce-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
