---
title: Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 5f0740af49bb369be87a1a33973b67f59acf3ab6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700826"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="bd9b5-102">Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bd9b5-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="bd9b5-103">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="bd9b5-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="bd9b5-104">Um cliente chamou uma propriedade ou método de um componente fora do processo e tentou passar uma referência a um objeto particular como um dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="bd9b5-105">Um componente fora do processo chamou um método de retorno de chamada em seu cliente e tentou passar uma referência a um objeto particular.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="bd9b5-106">Um componente fora do processo tentou passar uma referência a um objeto particular como um argumento de um evento que ele estava gerando.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="bd9b5-107">Um cliente tentou atribuir uma referência de objeto particular para um `ByRef` argumento de um evento que estava tratando.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd9b5-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="bd9b5-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="bd9b5-109">Remova a referência.</span><span class="sxs-lookup"><span data-stu-id="bd9b5-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd9b5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd9b5-110">See also</span></span>
- [<span data-ttu-id="bd9b5-111">Privado</span><span class="sxs-lookup"><span data-stu-id="bd9b5-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
