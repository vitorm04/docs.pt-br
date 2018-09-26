---
title: Expõe e chamar ActivityActions
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 99207c33d82ec9028da2355cc792c366dc5e0cc6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176393"
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="ebff4-102">Expõe e chamar ActivityActions</span><span class="sxs-lookup"><span data-stu-id="ebff4-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="ebff4-103">Este exemplo demonstra como desenvolver uma atividade personalizado que tem <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="ebff4-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="ebff4-104">Também demonstra como usar esta atividade fornecendo uma implementação de <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="ebff4-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="ebff4-105">Um <xref:System.Activities.ActivityAction> permite que um autor de atividade expõe "furos" com assinaturas específicas em que o usuário da atividade pode conectar um comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="ebff4-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="ebff4-106">Por exemplo, a atividade de <xref:System.Activities.Statements.ForEach%601> , (que opera em uma coleção de itens), tem <xref:System.Activities.ActivityAction> que permite que o usuário de atividade obstrua no comportamento que opera no item de iteração atual.</span><span class="sxs-lookup"><span data-stu-id="ebff4-106">For example, the <xref:System.Activities.Statements.ForEach%601> activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ebff4-107">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ebff4-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ebff4-108">Abra o **ActivityAction** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ebff4-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ebff4-109">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="ebff4-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ebff4-110">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ebff4-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ebff4-111">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ebff4-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ebff4-112">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ebff4-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ebff4-113">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ebff4-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`