---
title: "A função &quot;Dir&quot; deve ser chamada primeiro com um argumento &quot;PathName&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDIR_IllegalCall
dev_langs:
- VB
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b957e384c8cf099aed300f42ece804996c48371b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a><span data-ttu-id="f968d-102">A função 'Dir' deve ser chamada primeiro com um argumento 'PathName'</span><span class="sxs-lookup"><span data-stu-id="f968d-102">&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument</span></span>
<span data-ttu-id="f968d-103">Uma chamada inicial para o `Dir` função não inclui o `PathName` argumento.</span><span class="sxs-lookup"><span data-stu-id="f968d-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="f968d-104">A primeira chamada para `Dir` deve incluir uma `PathName`, mas subsequentes chamadas para `Dir` não precisa incluir parâmetros para recuperar o próximo item.</span><span class="sxs-lookup"><span data-stu-id="f968d-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f968d-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f968d-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="f968d-106">Forneça um `PathName` argumento na chamada de função.</span><span class="sxs-lookup"><span data-stu-id="f968d-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f968d-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f968d-107">See Also</span></span>  
 <span data-ttu-id="f968d-108"><xref:Microsoft.VisualBasic.FileSystem.Dir%2A></xref:Microsoft.VisualBasic.FileSystem.Dir%2A></span><span class="sxs-lookup"><span data-stu-id="f968d-108"><xref:Microsoft.VisualBasic.FileSystem.Dir%2A></span></span>
