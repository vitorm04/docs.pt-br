---
title: "Expõe e chamar ActivityActions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 45920f913a1d7252858fd0e563da944c10fae75c
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="6096f-102">Expõe e chamar ActivityActions</span><span class="sxs-lookup"><span data-stu-id="6096f-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="6096f-103">Este exemplo demonstra como desenvolver uma atividade personalizado que tem <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="6096f-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="6096f-104">Também demonstra como usar esta atividade fornecendo uma implementação de <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="6096f-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="6096f-105">Um <xref:System.Activities.ActivityAction> permite que um autor de atividade expõem "intervalos" com assinaturas específicas em que o usuário de atividade pode conectar um comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="6096f-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="6096f-106">Por exemplo, o <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` atividade, (que opera em uma coleção de itens), tem um <xref:System.Activities.ActivityAction> que permite que o usuário de atividade de comportamento que opera no item de iteração atual.</span><span class="sxs-lookup"><span data-stu-id="6096f-106">For example, the <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6096f-107">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6096f-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6096f-108">Abra o **ActivityAction.sln** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6096f-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="6096f-109">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="6096f-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6096f-110">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6096f-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6096f-111">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="6096f-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6096f-112">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="6096f-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6096f-113">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="6096f-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`