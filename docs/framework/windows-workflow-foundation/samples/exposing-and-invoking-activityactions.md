---
title: Expõe e chamar ActivityActions
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 2d369ec4b028b047ce02016dd511c1c088b46a91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513146"
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="0a488-102">Expõe e chamar ActivityActions</span><span class="sxs-lookup"><span data-stu-id="0a488-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="0a488-103">Este exemplo demonstra como desenvolver uma atividade personalizado que tem <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="0a488-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="0a488-104">Também demonstra como usar esta atividade fornecendo uma implementação de <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="0a488-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="0a488-105">Um <xref:System.Activities.ActivityAction> permite que um autor de atividade expõem "intervalos" com assinaturas específicas em que o usuário de atividade pode conectar um comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="0a488-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="0a488-106">Por exemplo, o <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` atividade, (que opera em uma coleção de itens), tem um <xref:System.Activities.ActivityAction> que permite que o usuário de atividade de comportamento que opera no item de iteração atual.</span><span class="sxs-lookup"><span data-stu-id="0a488-106">For example, the <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0a488-107">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0a488-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0a488-108">Abra o **ActivityAction.sln** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0a488-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="0a488-109">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="0a488-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0a488-110">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0a488-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0a488-111">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0a488-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0a488-112">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0a488-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0a488-113">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0a488-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`