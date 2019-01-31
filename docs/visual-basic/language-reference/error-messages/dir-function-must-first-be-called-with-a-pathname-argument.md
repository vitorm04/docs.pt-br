---
title: A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 828c715d9aaceef17d030113e7eda302f025ca9d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282576"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="36061-102">A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'</span><span class="sxs-lookup"><span data-stu-id="36061-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="36061-103">Uma chamada inicial para o `Dir` função não inclui o `PathName` argumento.</span><span class="sxs-lookup"><span data-stu-id="36061-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="36061-104">A primeira chamada para `Dir` deve incluir uma `PathName`, as chamadas subsequentes, mas para `Dir` não precisa incluir parâmetros para recuperar o próximo item.</span><span class="sxs-lookup"><span data-stu-id="36061-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="36061-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="36061-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="36061-106">Forneça um `PathName` argumento na chamada de função.</span><span class="sxs-lookup"><span data-stu-id="36061-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36061-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36061-107">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
