---
title: Não foi possível obter o nome do sistema completo de operação devido a erro interno
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: f85ca5f7f325cb0dd2b8fc55d3f90f6abdfd4a7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="852f7-102">Não foi possível obter o nome do sistema completo de operação devido a erro interno</span><span class="sxs-lookup"><span data-stu-id="852f7-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="852f7-103">Não foi possível obter o nome do sistema completo de operação devido a erro interno.</span><span class="sxs-lookup"><span data-stu-id="852f7-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="852f7-104">Isso pode ser causado pelo WMI não existentes no computador atual.</span><span class="sxs-lookup"><span data-stu-id="852f7-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="852f7-105">Uma chamada para o `My.Computer.Info.OSFullName` propriedade falhou.</span><span class="sxs-lookup"><span data-stu-id="852f7-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="852f7-106">Uma possível causa dessa falha é se o Windows Management Instrumentation (WMI) não está instalado no computador atual.</span><span class="sxs-lookup"><span data-stu-id="852f7-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="852f7-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="852f7-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="852f7-108">Adicionar um `Try...Catch` em torno da chamada para o `My.Computer.Info.OSFullName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="852f7-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="852f7-109">Para obter mais informações sobre WMI e como instalá-lo, vá para e procure "Windows Management Instrumentation Core".</span><span class="sxs-lookup"><span data-stu-id="852f7-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="852f7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="852f7-110">See Also</span></span>  
 [<span data-ttu-id="852f7-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="852f7-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="852f7-112">Exceção e tratamento de erros no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="852f7-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="852f7-113">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="852f7-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
