---
title: "Exemplo compensável de atividades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b8d7fb5650a8927016e0deebc07a68a8145496db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="compensable-activity-sample"></a><span data-ttu-id="0ae30-102">Exemplo compensável de atividades</span><span class="sxs-lookup"><span data-stu-id="0ae30-102">Compensable Activity Sample</span></span>
<span data-ttu-id="0ae30-103">Este exemplo demonstra como usar a atividade de `CompensableActivity` para definir o trabalho a ser feitos se necessário para uma determinada ação durante a execução normal e o trabalho que é necessário para ser feito para compensar essa ação, mais tarde.</span><span class="sxs-lookup"><span data-stu-id="0ae30-103">This sample demonstrates how to use the `CompensableActivity` activity to define the work to be done for a given action during normal execution and the work that is necessary to be done to compensate that action, if necessary at a later time.</span></span>  <span data-ttu-id="0ae30-104">A primeira parte do exemplo mostra como as unidades de trabalho compensável podem ser definidas em [!INCLUDE[wf](../../../../includes/wf-md.md)] usando uma atividade de `CompensableActivity` e como eles são executadas em uma execução bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ae30-104">The first part of the sample shows how units of compensable work can be defined in [!INCLUDE[wf](../../../../includes/wf-md.md)] using a `CompensableActivity` activity and how they are executed in a successful run.</span></span>  <span data-ttu-id="0ae30-105">A segunda parte do exemplo mostra como as mesmas unidades de trabalho compensável recebem automaticamente de compensação inesperado quando um evento é atingido e a instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="0ae30-105">The second part of the sample shows how the same units of compensable work automatically take care of compensation when an unexpected event is hit and the workflow instance is canceled.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0ae30-106">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0ae30-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0ae30-107">Usando o Visual Studio 2010, abra o CompensableActivity.sln.</span><span class="sxs-lookup"><span data-stu-id="0ae30-107">Using Visual Studio 2010, open the CompensableActivity.sln.</span></span>  
  
2.  <span data-ttu-id="0ae30-108">Crie a solução. CTRL+SHIFT+B pressionando.</span><span class="sxs-lookup"><span data-stu-id="0ae30-108">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="0ae30-109">Executar o aplicativo pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="0ae30-109">Run the application by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0ae30-110">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0ae30-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0ae30-111">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0ae30-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0ae30-112">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0ae30-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0ae30-113">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0ae30-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`  
  
## <a name="see-also"></a><span data-ttu-id="0ae30-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ae30-114">See Also</span></span>
