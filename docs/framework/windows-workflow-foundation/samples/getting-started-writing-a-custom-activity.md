---
title: "Introdução ao escrever uma atividade personalizado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4921f9f2dbfb8405019a5bc0c0b8242ea66f2db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="0e8f8-102">Introdução ao escrever uma atividade personalizado</span><span class="sxs-lookup"><span data-stu-id="0e8f8-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="0e8f8-103">Este exemplo demonstra como definir uma atividade personalizado simples em XAML.</span><span class="sxs-lookup"><span data-stu-id="0e8f8-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="0e8f8-104">A atividade é dada o nome `Rhyme`, e sua lógica é uma sequência de três atividades de <xref:System.Activities.Statements.WriteLine> .</span><span class="sxs-lookup"><span data-stu-id="0e8f8-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0e8f8-105">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0e8f8-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0e8f8-106">Abra o **Simple.sln** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e8f8-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="0e8f8-107">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="0e8f8-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0e8f8-108">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0e8f8-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0e8f8-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0e8f8-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0e8f8-110">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0e8f8-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0e8f8-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0e8f8-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`  
  
## <a name="see-also"></a><span data-ttu-id="0e8f8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e8f8-112">See Also</span></span>
