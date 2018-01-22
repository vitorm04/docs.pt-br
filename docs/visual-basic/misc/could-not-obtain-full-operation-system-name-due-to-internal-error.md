---
title: "Não foi possível obter o nome do sistema completo de operação devido a erro interno"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e90de5a2fd0699a449e05b9c32e7450b8bdc991
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="1da65-102">Não foi possível obter o nome do sistema completo de operação devido a erro interno</span><span class="sxs-lookup"><span data-stu-id="1da65-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="1da65-103">Não foi possível obter o nome do sistema completo de operação devido a erro interno.</span><span class="sxs-lookup"><span data-stu-id="1da65-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="1da65-104">Isso pode ser causado pelo WMI não existentes no computador atual.</span><span class="sxs-lookup"><span data-stu-id="1da65-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="1da65-105">Uma chamada para o `My.Computer.Info.OSFullName` propriedade falhou.</span><span class="sxs-lookup"><span data-stu-id="1da65-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="1da65-106">Uma possível causa dessa falha é se o Windows Management Instrumentation (WMI) não está instalado no computador atual.</span><span class="sxs-lookup"><span data-stu-id="1da65-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1da65-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1da65-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="1da65-108">Adicionar um `Try...Catch` em torno da chamada para o `My.Computer.Info.OSFullName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="1da65-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="1da65-109">Para obter mais informações sobre WMI e como instalá-lo, vá para e procure "Windows Management Instrumentation Core".</span><span class="sxs-lookup"><span data-stu-id="1da65-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da65-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1da65-110">See Also</span></span>  
 [<span data-ttu-id="1da65-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="1da65-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="1da65-112">Exceção e tratamento de erros no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1da65-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="1da65-113">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="1da65-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
