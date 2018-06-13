---
title: Usando uma atividade do .NET Framework 3.0 ou do.NET Framework 3.5 em um fluxo de trabalho do .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
ms.openlocfilehash: ab2e93918617bd1ca21fb32878d446db0dd2ef16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514893"
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a><span data-ttu-id="a0584-102">Usando uma atividade do .NET Framework 3.0 ou do.NET Framework 3.5 em um fluxo de trabalho do .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="a0584-102">Using a .NET Framework 3.0 or .NET Framework 3.5 Activity in a .NET Framework 4.5 Workflow</span></span>
<span data-ttu-id="a0584-103">O <xref:System.Activities.Statements.Interop> atividade permite que você execute uma atividade do .NET Framework 3.0 Windows Workflow Foundation (WF) dentro de um [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a0584-103">The <xref:System.Activities.Statements.Interop> activity allows you to run a .NET Framework 3.0 Windows Workflow Foundation (WF) activity within a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="a0584-104">Este exemplo demonstra como usar a atividade de <xref:System.Activities.Statements.Interop> para passar uma cadeia de caracteres como um argumento para uma atividade personalizado de [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a0584-104">This sample demonstrates how to use the <xref:System.Activities.Statements.Interop> activity to pass a string as an argument to a custom [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] activity.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="a0584-105">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="a0584-105">To use this sample</span></span>  
  
1.  <span data-ttu-id="a0584-106">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de SimpleInterop.sln.</span><span class="sxs-lookup"><span data-stu-id="a0584-106">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the SimpleInterop.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a0584-107">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="a0584-107">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a0584-108">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="a0584-108">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0584-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a0584-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a0584-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a0584-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a0584-111">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a0584-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a0584-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a0584-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a><span data-ttu-id="a0584-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0584-113">See Also</span></span>
