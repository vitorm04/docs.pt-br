---
title: "Convenção de chamada de DLL incorreta | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID49
dev_langs:
- VB
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
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
ms.openlocfilehash: e9f1aedd9921a468567ea68fa44ccead734db909
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="26b07-102">Convenção de chamada de DLL inválida</span><span class="sxs-lookup"><span data-stu-id="26b07-102">Bad DLL calling convention</span></span>
<span data-ttu-id="26b07-103">Argumentos passados para uma biblioteca de vínculo dinâmico (DLL) devem corresponder exatamente àqueles esperado pela rotina.</span><span class="sxs-lookup"><span data-stu-id="26b07-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="26b07-104">Convenções de chamada lidam com número, tipo e ordem dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="26b07-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="26b07-105">Seu programa pode ser chamando uma rotina em uma DLL que é passada a tipo errado ou o número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="26b07-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="26b07-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="26b07-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="26b07-107">Verifique se que todos os tipos de argumento de acordo com aquelas especificadas na declaração de rotina que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="26b07-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="26b07-108">Verifique se que você está passando o mesmo número de argumentos indicado na declaração de rotina que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="26b07-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="26b07-109">Se a rotina DLL espera argumentos por valor, certifique-se `ByVal` é especificado para esses argumentos na declaração para a rotina.</span><span class="sxs-lookup"><span data-stu-id="26b07-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b07-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26b07-110">See Also</span></span>  
 <span data-ttu-id="26b07-111">[Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md) </span><span class="sxs-lookup"><span data-stu-id="26b07-111">[Error Types](../../../visual-basic/programming-guide/language-features/error-types.md) </span></span>  
<span data-ttu-id="26b07-112"> [Instrução Call](../../../visual-basic/language-reference/statements/call-statement.md) </span><span class="sxs-lookup"><span data-stu-id="26b07-112"> [Call Statement](../../../visual-basic/language-reference/statements/call-statement.md) </span></span>  
<span data-ttu-id="26b07-113"> [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)</span><span class="sxs-lookup"><span data-stu-id="26b07-113"> [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)</span></span>
