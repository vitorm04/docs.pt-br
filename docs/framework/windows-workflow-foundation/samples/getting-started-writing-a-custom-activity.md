---
title: Introdução ao escrever uma atividade personalizado
ms.date: 03/30/2017
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
ms.openlocfilehash: 1c455009a0c658429c13da5e93d07c744402dd61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513301"
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="037b5-102">Introdução ao escrever uma atividade personalizado</span><span class="sxs-lookup"><span data-stu-id="037b5-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="037b5-103">Este exemplo demonstra como definir uma atividade personalizado simples em XAML.</span><span class="sxs-lookup"><span data-stu-id="037b5-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="037b5-104">A atividade é dada o nome `Rhyme`, e sua lógica é uma sequência de três atividades de <xref:System.Activities.Statements.WriteLine> .</span><span class="sxs-lookup"><span data-stu-id="037b5-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="037b5-105">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="037b5-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="037b5-106">Abra o **Simple.sln** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="037b5-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="037b5-107">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="037b5-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="037b5-108">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="037b5-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="037b5-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="037b5-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="037b5-110">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="037b5-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="037b5-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="037b5-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`