---
title: Não foi possível obter o nome do sistema de operação completa devido a erro interno
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: ecbed5b59d36b1984c0b0ae161821ea99d28e090
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970580"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="41028-102">Não foi possível obter o nome do sistema de operação completa devido a erro interno</span><span class="sxs-lookup"><span data-stu-id="41028-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="41028-103">Não foi possível obter o nome do sistema de operação completa devido a erro interno.</span><span class="sxs-lookup"><span data-stu-id="41028-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="41028-104">Isso pode ser causado pelo WMI não existente no computador atual.</span><span class="sxs-lookup"><span data-stu-id="41028-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="41028-105">Uma chamada para o `My.Computer.Info.OSFullName` propriedade falhou.</span><span class="sxs-lookup"><span data-stu-id="41028-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="41028-106">Uma possível causa dessa falha é se o Windows Management Instrumentation (WMI) não está instalado no computador atual.</span><span class="sxs-lookup"><span data-stu-id="41028-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="41028-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="41028-107">To correct this error</span></span>  
  
1. <span data-ttu-id="41028-108">Adicionar um `Try...Catch` bloco em torno da chamada para o `My.Computer.Info.OSFullName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="41028-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="41028-109">Para obter mais informações sobre o WMI e como instalá-lo, vá para e pesquise por "Core de instrumentação de gerenciamento do Windows".</span><span class="sxs-lookup"><span data-stu-id="41028-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41028-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41028-110">See also</span></span>

- [<span data-ttu-id="41028-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="41028-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="41028-112">Tratando e gerando exceções no .NET</span><span class="sxs-lookup"><span data-stu-id="41028-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="41028-113">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="41028-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
