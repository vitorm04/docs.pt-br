---
title: "'Optional' esperado"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 71a25784f357a7e596093b314ed5b3d721d6f92c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341875"
---
# <a name="optional-expected"></a><span data-ttu-id="51196-102">'Optional' esperado</span><span class="sxs-lookup"><span data-stu-id="51196-102">'Optional' expected</span></span>
<span data-ttu-id="51196-103">Um argumento opcional em uma declaração de procedimento é seguido por um argumento obrigatório.</span><span class="sxs-lookup"><span data-stu-id="51196-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="51196-104">Cada argumento após um argumento opcional também deve ser opcional.</span><span class="sxs-lookup"><span data-stu-id="51196-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="51196-105">**ID do erro:** BC30202</span><span class="sxs-lookup"><span data-stu-id="51196-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="51196-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="51196-106">To correct this error</span></span>  
  
1. <span data-ttu-id="51196-107">Se o argumento deve ser necessária, movê-la para preceder o primeiro argumento opcional na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="51196-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="51196-108">Se o argumento deve ser opcional, use o `Optional` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="51196-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51196-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51196-109">See also</span></span>

- [<span data-ttu-id="51196-110">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="51196-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
