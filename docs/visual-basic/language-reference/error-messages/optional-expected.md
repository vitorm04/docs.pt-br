---
title: "'Optional' esperado"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: e212939cf814a9ac632571b2203f2f256dea61ae
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873598"
---
# <a name="optional-expected"></a><span data-ttu-id="77ccf-102">'Optional' esperado</span><span class="sxs-lookup"><span data-stu-id="77ccf-102">'Optional' expected</span></span>

<span data-ttu-id="77ccf-103">Um argumento opcional em uma declaração de procedimento é seguido por um argumento necessário.</span><span class="sxs-lookup"><span data-stu-id="77ccf-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="77ccf-104">Todos os argumentos após um argumento opcional também devem ser opcionais.</span><span class="sxs-lookup"><span data-stu-id="77ccf-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="77ccf-105">**ID do erro:** BC30202</span><span class="sxs-lookup"><span data-stu-id="77ccf-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="77ccf-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="77ccf-106">To correct this error</span></span>  
  
1. <span data-ttu-id="77ccf-107">Se o argumento se destinar a ser necessário, mova-o para preceder o primeiro argumento opcional na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="77ccf-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="77ccf-108">Se o argumento se destinar a ser opcional, use a `Optional` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="77ccf-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ccf-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="77ccf-109">See also</span></span>

- [<span data-ttu-id="77ccf-110">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="77ccf-110">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
