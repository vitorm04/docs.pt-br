---
title: Não foi possível obter o nome do sistema completo de operação devido a erro interno
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 67e8fb5e906800d28bf15714463b7ff6ae585693
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402272"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="85a29-102">Não foi possível obter o nome do sistema completo de operação devido a erro interno</span><span class="sxs-lookup"><span data-stu-id="85a29-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="85a29-103">Não foi possível obter o nome completo do sistema operacional devido a um erro interno.</span><span class="sxs-lookup"><span data-stu-id="85a29-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="85a29-104">Isso pode ser causado por WMI não existente no computador atual.</span><span class="sxs-lookup"><span data-stu-id="85a29-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="85a29-105">Falha em uma chamada para a `My.Computer.Info.OSFullName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="85a29-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="85a29-106">Uma possível causa dessa falha é se a Instrumentação de Gerenciamento do Windows (WMI) não estiver instalada no computador atual.</span><span class="sxs-lookup"><span data-stu-id="85a29-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="85a29-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="85a29-107">To correct this error</span></span>  
  
1. <span data-ttu-id="85a29-108">Adicione um `Try...Catch` bloco em volta da chamada para a `My.Computer.Info.OSFullName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="85a29-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="85a29-109">Para obter mais informações sobre o WMI e como instalá-lo, vá para e pesquise "Instrumentação de Gerenciamento do Windows Core".</span><span class="sxs-lookup"><span data-stu-id="85a29-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a29-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="85a29-110">See also</span></span>

- [<span data-ttu-id="85a29-111">My. Computer. info. OSFullName</span><span class="sxs-lookup"><span data-stu-id="85a29-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="85a29-112">Tratando e gerando exceções no .NET</span><span class="sxs-lookup"><span data-stu-id="85a29-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="85a29-113">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="85a29-113">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
