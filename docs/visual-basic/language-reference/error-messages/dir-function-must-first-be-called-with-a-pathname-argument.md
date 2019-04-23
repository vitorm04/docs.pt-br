---
title: A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: d255b8dddd098835764f72b8a166eaa08b0353df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767884"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="8c682-102">A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'</span><span class="sxs-lookup"><span data-stu-id="8c682-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="8c682-103">Uma chamada inicial para o `Dir` função não inclui o `PathName` argumento.</span><span class="sxs-lookup"><span data-stu-id="8c682-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="8c682-104">A primeira chamada para `Dir` deve incluir uma `PathName`, as chamadas subsequentes, mas para `Dir` não precisa incluir parâmetros para recuperar o próximo item.</span><span class="sxs-lookup"><span data-stu-id="8c682-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8c682-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8c682-105">To correct this error</span></span>  
  
1. <span data-ttu-id="8c682-106">Forneça um `PathName` argumento na chamada de função.</span><span class="sxs-lookup"><span data-stu-id="8c682-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c682-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c682-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
