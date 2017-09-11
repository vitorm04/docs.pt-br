---
title: "Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou como um valor de retorno | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID98
dev_langs:
- VB
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f04f20c7fa97cb3f0cce2b1a30066b489f747528
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="4b796-102">Uma chamada de propriedade ou método não pode incluir uma referência a um objeto particular, como um argumento ou um valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4b796-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="4b796-103">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="4b796-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="4b796-104">Um cliente chamou uma propriedade ou método de um componente fora de processo e tentou passar uma referência a um objeto particular como um dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="4b796-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="4b796-105">Um componente fora de processo chamou um método de retorno de chamada no seu cliente e tentou passar uma referência a um objeto particular.</span><span class="sxs-lookup"><span data-stu-id="4b796-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="4b796-106">Um componente fora de processo tentou passar uma referência a um objeto particular como um argumento de um evento que ele estava lançando.</span><span class="sxs-lookup"><span data-stu-id="4b796-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="4b796-107">Um cliente tentou atribuir uma referência de objeto particular para um `ByRef` argumento de um evento que ele estava tratando.</span><span class="sxs-lookup"><span data-stu-id="4b796-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4b796-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4b796-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="4b796-109">Remova a referência.</span><span class="sxs-lookup"><span data-stu-id="4b796-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b796-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b796-110">See Also</span></span>  
 [<span data-ttu-id="4b796-111">Privado</span><span class="sxs-lookup"><span data-stu-id="4b796-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
