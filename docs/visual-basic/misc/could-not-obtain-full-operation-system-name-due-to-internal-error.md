---
title: "Não foi possível obter o nome do sistema completo de operação devido a erro interno | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 9
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
ms.openlocfilehash: 21ef85e446a108165424fd134013a122e2b81391
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="61564-102">Não foi possível obter o nome do sistema completo de operação devido a erro interno</span><span class="sxs-lookup"><span data-stu-id="61564-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="61564-103">Não foi possível obter o nome do sistema completo de operação devido a erro interno.</span><span class="sxs-lookup"><span data-stu-id="61564-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="61564-104">Isso pode ser causado pelo WMI não existentes no computador atual.</span><span class="sxs-lookup"><span data-stu-id="61564-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="61564-105">Uma chamada para o `My.Computer.Info.OSFullName` propriedade falhou.</span><span class="sxs-lookup"><span data-stu-id="61564-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="61564-106">Uma possível causa dessa falha é se o Windows Management Instrumentation (WMI) não está instalado no computador atual.</span><span class="sxs-lookup"><span data-stu-id="61564-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="61564-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="61564-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="61564-108">Adicionar uma `Try...Catch` em torno da chamada para o `My.Computer.Info.OSFullName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="61564-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="61564-109">Para obter mais informações sobre o WMI e como instalá-lo, vá para e procure "Windows Management Instrumentation Core".</span><span class="sxs-lookup"><span data-stu-id="61564-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61564-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61564-110">See Also</span></span>  
 <span data-ttu-id="61564-111">[Propriedade My.Computer.Info.OSFullName](http://msdn.microsoft.com/en-us/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be) </span><span class="sxs-lookup"><span data-stu-id="61564-111">[My.Computer.Info.OSFullName Property](http://msdn.microsoft.com/en-us/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be) </span></span>  
<span data-ttu-id="61564-112"> [Exceção e tratamento de erros no Visual Basic](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e) </span><span class="sxs-lookup"><span data-stu-id="61564-112"> [Exception and Error Handling in Visual Basic](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e) </span></span>  
<span data-ttu-id="61564-113"> [Instrução Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)</span><span class="sxs-lookup"><span data-stu-id="61564-113"> [Try...Catch...Finally Statement](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)</span></span>
