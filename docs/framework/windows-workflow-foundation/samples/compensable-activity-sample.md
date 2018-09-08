---
title: Exemplo compensável de atividades
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 3bf1d120cd700830a98f53495f7e9989ffec73db
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131371"
---
# <a name="compensable-activity-sample"></a><span data-ttu-id="d44bd-102">Exemplo compensável de atividades</span><span class="sxs-lookup"><span data-stu-id="d44bd-102">Compensable Activity Sample</span></span>
<span data-ttu-id="d44bd-103">Este exemplo demonstra como usar a atividade de `CompensableActivity` para definir o trabalho a ser feitos se necessário para uma determinada ação durante a execução normal e o trabalho que é necessário para ser feito para compensar essa ação, mais tarde.</span><span class="sxs-lookup"><span data-stu-id="d44bd-103">This sample demonstrates how to use the `CompensableActivity` activity to define the work to be done for a given action during normal execution and the work that is necessary to be done to compensate that action, if necessary at a later time.</span></span>  <span data-ttu-id="d44bd-104">A primeira parte do exemplo mostra como unidades de trabalho compensável podem ser definidas no Windows Workflow Foundation (WF) usando um `CompensableActivity` atividade e como eles são executados em uma execução bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d44bd-104">The first part of the sample shows how units of compensable work can be defined in Windows Workflow Foundation (WF) using a `CompensableActivity` activity and how they are executed in a successful run.</span></span>  <span data-ttu-id="d44bd-105">A segunda parte do exemplo mostra como as mesmas unidades de trabalho compensável recebem automaticamente de compensação inesperado quando um evento é atingido e a instância de fluxo de trabalho é cancelada.</span><span class="sxs-lookup"><span data-stu-id="d44bd-105">The second part of the sample shows how the same units of compensable work automatically take care of compensation when an unexpected event is hit and the workflow instance is canceled.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d44bd-106">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="d44bd-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d44bd-107">Usando o Visual Studio 2010, abra o CompensableActivity.sln.</span><span class="sxs-lookup"><span data-stu-id="d44bd-107">Using Visual Studio 2010, open the CompensableActivity.sln.</span></span>  
  
2.  <span data-ttu-id="d44bd-108">Crie a solução. CTRL+SHIFT+B pressionando.</span><span class="sxs-lookup"><span data-stu-id="d44bd-108">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="d44bd-109">Executar o aplicativo pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="d44bd-109">Run the application by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d44bd-110">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d44bd-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d44bd-111">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d44bd-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d44bd-112">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="d44bd-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d44bd-113">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d44bd-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`