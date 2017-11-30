---
title: "Convenção de chamada de DLL inválida"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="7ed65-102">Convenção de chamada de DLL inválida</span><span class="sxs-lookup"><span data-stu-id="7ed65-102">Bad DLL calling convention</span></span>
<span data-ttu-id="7ed65-103">Argumentos passados para uma biblioteca de vínculo dinâmico (DLL) devem corresponder exatamente àqueles esperado pela rotina.</span><span class="sxs-lookup"><span data-stu-id="7ed65-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="7ed65-104">Convenções de chamada lidam com número, tipo e ordem dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="7ed65-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="7ed65-105">Seu programa pode chamar uma rotina em uma DLL que está sendo passada o tipo incorreto ou o número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="7ed65-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7ed65-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7ed65-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="7ed65-107">Verifique se que todos os tipos de argumento de acordo com aquelas especificadas na declaração de rotina que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="7ed65-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="7ed65-108">Verifique se que você estiver passando o mesmo número de argumentos indicado na declaração de rotina que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="7ed65-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="7ed65-109">Se a rotina DLL espera argumentos por valor, certifique-se de `ByVal` é especificado para esses argumentos na declaração para a rotina.</span><span class="sxs-lookup"><span data-stu-id="7ed65-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed65-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ed65-110">See Also</span></span>  
 [<span data-ttu-id="7ed65-111">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="7ed65-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="7ed65-112">Instrução Call</span><span class="sxs-lookup"><span data-stu-id="7ed65-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)  
 [<span data-ttu-id="7ed65-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="7ed65-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
