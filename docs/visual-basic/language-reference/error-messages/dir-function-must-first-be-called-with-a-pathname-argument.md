---
title: A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1a5d6ed145199ae995a98b6c1180fa3aedf9942c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834147"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="32ff8-102">A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'</span><span class="sxs-lookup"><span data-stu-id="32ff8-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="32ff8-103">Uma chamada inicial para o `Dir` função não inclui o `PathName` argumento.</span><span class="sxs-lookup"><span data-stu-id="32ff8-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="32ff8-104">A primeira chamada para `Dir` deve incluir uma `PathName`, as chamadas subsequentes, mas para `Dir` não precisa incluir parâmetros para recuperar o próximo item.</span><span class="sxs-lookup"><span data-stu-id="32ff8-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="32ff8-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="32ff8-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="32ff8-106">Forneça um `PathName` argumento na chamada de função.</span><span class="sxs-lookup"><span data-stu-id="32ff8-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ff8-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32ff8-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
