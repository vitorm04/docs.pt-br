---
title: A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1064a44f7c266b9dcce05dfddedef6bb1e919999
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874455"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="086b0-102">A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'</span><span class="sxs-lookup"><span data-stu-id="086b0-102">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="086b0-103">Uma chamada inicial para a `Dir` função não inclui o `PathName` argumento.</span><span class="sxs-lookup"><span data-stu-id="086b0-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="086b0-104">A primeira chamada para `Dir` deve incluir uma `PathName` , mas as chamadas subsequentes para não `Dir` precisam incluir parâmetros para recuperar o próximo item.</span><span class="sxs-lookup"><span data-stu-id="086b0-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="086b0-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="086b0-105">To correct this error</span></span>  
  
1. <span data-ttu-id="086b0-106">Forneça um `PathName` argumento na chamada de função.</span><span class="sxs-lookup"><span data-stu-id="086b0-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="086b0-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="086b0-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
