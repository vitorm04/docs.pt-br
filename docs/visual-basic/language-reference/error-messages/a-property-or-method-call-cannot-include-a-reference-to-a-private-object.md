---
title: Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 1f36526eab1bc0964bf89398b6e0f3e74d09fdc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583819"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="c9f21-102">Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c9f21-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="c9f21-103">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="c9f21-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="c9f21-104">Um cliente chamou uma propriedade ou método de um componente fora de processo e tentou passar uma referência a um objeto particular como um dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="c9f21-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="c9f21-105">Um componente fora do processo chamou um método de retorno de chamada no seu cliente e tentou passar uma referência a um objeto particular.</span><span class="sxs-lookup"><span data-stu-id="c9f21-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="c9f21-106">Um componente fora de processo tentou passar uma referência a um objeto particular como um argumento de um evento que ele estava lançando.</span><span class="sxs-lookup"><span data-stu-id="c9f21-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="c9f21-107">Um cliente tentou atribuir uma referência de objeto particular para um `ByRef` argumento de um evento que ele estava tratando.</span><span class="sxs-lookup"><span data-stu-id="c9f21-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c9f21-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c9f21-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="c9f21-109">Remova a referência.</span><span class="sxs-lookup"><span data-stu-id="c9f21-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f21-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9f21-110">See Also</span></span>  
 [<span data-ttu-id="c9f21-111">Privado</span><span class="sxs-lookup"><span data-stu-id="c9f21-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
