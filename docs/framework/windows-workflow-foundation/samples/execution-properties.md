---
title: Propriedades de execução
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 4906c2ad11c8b5822764435d2b39a5b51f2673ba
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748188"
---
# <a name="execution-properties"></a><span data-ttu-id="65fa0-102">Propriedades de execução</span><span class="sxs-lookup"><span data-stu-id="65fa0-102">Execution Properties</span></span>
<span data-ttu-id="65fa0-103">Este exemplo mostra como definir e usar uma propriedade de execução em uma atividade personalizado.</span><span class="sxs-lookup"><span data-stu-id="65fa0-103">This sample shows how to define and use an execution property in a custom activity.</span></span> <span data-ttu-id="65fa0-104">Nesse exemplo, a propriedade de execução determina a cor do console de primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="65fa0-104">In this example, the execution property determines the console's foreground color.</span></span> <span data-ttu-id="65fa0-105">Um fluxo de trabalho do exemplo mostra como caminhos lógicos diferentes de execução (ramificações de uma atividade de <xref:System.Activities.Statements.Parallel> ) podem manter diferentes cores de console independentemente de execução intercalada de atividades (através das ramificações de atividade de <xref:System.Activities.Statements.Parallel> ).</span><span class="sxs-lookup"><span data-stu-id="65fa0-105">An example workflow shows how different logical paths of execution (branches of a <xref:System.Activities.Statements.Parallel> activity) can maintain different console colors despite interleaved execution of activities (across the branches of the <xref:System.Activities.Statements.Parallel> activity).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="65fa0-106">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="65fa0-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="65fa0-107">Abra a solução de exemplo de ExecutionProperties.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65fa0-107">Open the ExecutionProperties.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65fa0-108">Exibir ThreeColors.xaml antes de criar a solução exibe um erro, porque as atividades personalizados usadas devem ser compiladas ao mesmo tempo que a solução.</span><span class="sxs-lookup"><span data-stu-id="65fa0-108">Viewing ThreeColors.xaml before building the solution displays an error, because the custom activities used must be built at the same time as the solution.</span></span>  
  
2.  <span data-ttu-id="65fa0-109">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="65fa0-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="65fa0-110">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="65fa0-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="65fa0-111">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="65fa0-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="65fa0-112">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="65fa0-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="65fa0-113">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="65fa0-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`