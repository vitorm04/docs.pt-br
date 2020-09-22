---
title: Convenção de chamada de DLL inválida
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 0481bd5e4dfe7a24dff454d0754b519509fa967f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875738"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="7275e-102">Convenção de chamada de DLL inválida</span><span class="sxs-lookup"><span data-stu-id="7275e-102">Bad DLL calling convention</span></span>

<span data-ttu-id="7275e-103">Os argumentos passados para uma DLL (biblioteca de vínculo dinâmico) devem corresponder exatamente aos esperados pela rotina.</span><span class="sxs-lookup"><span data-stu-id="7275e-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="7275e-104">As convenções de chamada lidam com número, tipo e ordem de argumentos.</span><span class="sxs-lookup"><span data-stu-id="7275e-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="7275e-105">Seu programa pode estar chamando uma rotina em uma DLL que está recebendo o tipo errado ou o número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="7275e-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7275e-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7275e-106">To correct this error</span></span>  
  
1. <span data-ttu-id="7275e-107">Verifique se todos os tipos de argumento concordam com aqueles especificados na declaração da rotina que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="7275e-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="7275e-108">Certifique-se de que você está passando o mesmo número de argumentos indicado na declaração da rotina que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="7275e-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="7275e-109">Se a rotina DLL espera argumentos por valor, certifique-se `ByVal` de que é especificado para esses argumentos na declaração para a rotina.</span><span class="sxs-lookup"><span data-stu-id="7275e-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7275e-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="7275e-110">See also</span></span>

- [<span data-ttu-id="7275e-111">Tipos de erro</span><span class="sxs-lookup"><span data-stu-id="7275e-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="7275e-112">Instrução Call</span><span class="sxs-lookup"><span data-stu-id="7275e-112">Call Statement</span></span>](../statements/call-statement.md)
- [<span data-ttu-id="7275e-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="7275e-113">Declare Statement</span></span>](../statements/declare-statement.md)
