---
title: '&#39;Opcional&#39; esperado'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 46bd84e2bcf5c5bea11a5c9d8b6e9254c49e3021
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642471"
---
# <a name="39optional39-expected"></a><span data-ttu-id="21d93-102">&#39;Opcional&#39; esperado</span><span class="sxs-lookup"><span data-stu-id="21d93-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="21d93-103">Um argumento opcional em uma declaração de procedimento é seguido por um argumento obrigatório.</span><span class="sxs-lookup"><span data-stu-id="21d93-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="21d93-104">Cada argumento após um argumento opcional também deve ser opcional.</span><span class="sxs-lookup"><span data-stu-id="21d93-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="21d93-105">**ID do erro:** BC30202</span><span class="sxs-lookup"><span data-stu-id="21d93-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="21d93-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="21d93-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="21d93-107">Se o argumento deve ser necessária, movê-la para preceder o primeiro argumento opcional na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="21d93-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="21d93-108">Se o argumento deve ser opcional, use o `Optional` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="21d93-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d93-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21d93-109">See also</span></span>
- [<span data-ttu-id="21d93-110">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="21d93-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
