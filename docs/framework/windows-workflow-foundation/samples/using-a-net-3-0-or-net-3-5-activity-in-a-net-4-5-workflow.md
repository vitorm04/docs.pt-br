---
title: Usando uma atividade do .NET Framework 3.0 ou do.NET Framework 3.5 em um fluxo de trabalho do .NET Framework 4.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64c0e4b6e84f442b6e34f0cbd442ae04e2a9d0b5
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a><span data-ttu-id="d1f03-102">Usando uma atividade do .NET Framework 3.0 ou do.NET Framework 3.5 em um fluxo de trabalho do .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="d1f03-102">Using a .NET Framework 3.0 or .NET Framework 3.5 Activity in a .NET Framework 4.5 Workflow</span></span>
<span data-ttu-id="d1f03-103">O <xref:System.Activities.Statements.Interop> atividade permite que você execute uma atividade do .NET Framework 3.0 Windows Workflow Foundation (WF) dentro de um [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d1f03-103">The <xref:System.Activities.Statements.Interop> activity allows you to run a .NET Framework 3.0 Windows Workflow Foundation (WF) activity within a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="d1f03-104">Este exemplo demonstra como usar a atividade de <xref:System.Activities.Statements.Interop> para passar uma cadeia de caracteres como um argumento para uma atividade personalizado de [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d1f03-104">This sample demonstrates how to use the <xref:System.Activities.Statements.Interop> activity to pass a string as an argument to a custom [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] activity.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="d1f03-105">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="d1f03-105">To use this sample</span></span>  
  
1.  <span data-ttu-id="d1f03-106">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de SimpleInterop.sln.</span><span class="sxs-lookup"><span data-stu-id="d1f03-106">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the SimpleInterop.sln solution file.</span></span>  
  
2.  <span data-ttu-id="d1f03-107">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="d1f03-107">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="d1f03-108">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="d1f03-108">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1f03-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d1f03-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d1f03-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d1f03-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d1f03-111">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="d1f03-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d1f03-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d1f03-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a><span data-ttu-id="d1f03-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1f03-113">See Also</span></span>
