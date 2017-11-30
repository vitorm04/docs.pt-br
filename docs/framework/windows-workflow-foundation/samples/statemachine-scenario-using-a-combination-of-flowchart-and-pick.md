---
title: "Cenário de StateMachine usando uma combinação de fluxograma e de picareta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4a4ff644367f0bcd6562bd8931406a11f39d62df
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a><span data-ttu-id="74561-102">Cenário de StateMachine usando uma combinação de fluxograma e de picareta</span><span class="sxs-lookup"><span data-stu-id="74561-102">StateMachine Scenario Using a Combination of FlowChart and Pick</span></span>
<span data-ttu-id="74561-103">Este exemplo demonstra como implementar um cenário simples de cronômetro usando uma combinação de atividades de <xref:System.Activities.Statements.Flowchart> e de <xref:System.Activities.Statements.Pick> .</span><span class="sxs-lookup"><span data-stu-id="74561-103">This sample demonstrates how to implement a simple stopwatch scenario using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span> <span data-ttu-id="74561-104">Using receber e envia dentro de atividade de picareta para escutar eventos de cronômetro.</span><span class="sxs-lookup"><span data-stu-id="74561-104">It uses Receive and Send within the Pick activity to listen for stopwatch events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74561-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="74561-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="74561-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="74561-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="74561-107">Se este diretório não existe, vá (página de download) baixar todos os exemplos de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="74561-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="74561-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="74561-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a><span data-ttu-id="74561-109">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="74561-109">Sample Details</span></span>  
 <span data-ttu-id="74561-110">A tabela a seguir lista os projetos neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="74561-110">The following table lists the projects in this sample.</span></span>  
  
|<span data-ttu-id="74561-111">Nome do projeto</span><span class="sxs-lookup"><span data-stu-id="74561-111">Project Name</span></span>|<span data-ttu-id="74561-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="74561-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="74561-113">StopWatchService</span><span class="sxs-lookup"><span data-stu-id="74561-113">StopWatchService</span></span>|<span data-ttu-id="74561-114">Este projeto contém a implementação de um computador de estado para o exemplo do cronômetro usando uma combinação de atividades de <xref:System.Activities.Statements.Flowchart> e de <xref:System.Activities.Statements.Pick> .</span><span class="sxs-lookup"><span data-stu-id="74561-114">This project contains the implementation of a state machine for the stopwatch sample using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span><br /><br /> <span data-ttu-id="74561-115">A atividade de <xref:System.Activities.Statements.Pick> tem 3 instruções de <xref:System.Activities.Statements.PickBranch> dentro de propriedade de <xref:System.Activities.Statements.Pick.Branches%2A> que escutam `GetStart`, `GetStop` e eventos de `GetOff` .</span><span class="sxs-lookup"><span data-stu-id="74561-115">The <xref:System.Activities.Statements.Pick> activity has 3 <xref:System.Activities.Statements.PickBranch> statements within the <xref:System.Activities.Statements.Pick.Branches%2A> property that listen for `GetStart`, `GetStop` and `GetOff` events.</span></span> <span data-ttu-id="74561-116">Baseado no evento de entrada, disparadores para um dos ramificações ativam e <xref:System.Activities.Statements.PickBranch.Action%2A> correspondente é disparado.</span><span class="sxs-lookup"><span data-stu-id="74561-116">Based on the incoming event, the triggers for one of the branches activate and the corresponding <xref:System.Activities.Statements.PickBranch.Action%2A> is triggered.</span></span> <span data-ttu-id="74561-117">Em <xref:System.Activities.Statements.PickBranch.Action%2A> propriedade, é <xref:System.Activities.Statements.Switch%601> instrução que avalia se a transição é uma transição legítima e se estiver, a propriedade de `currentState` é atualizado para o estado fazer a transição e enviado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="74561-117">In the <xref:System.Activities.Statements.PickBranch.Action%2A> property, there is a <xref:System.Activities.Statements.Switch%601> statement that evaluates whether the transition is a legitimate transition and if it is, the `currentState` property is updated to the transitioning state and sent to the client.</span></span><br /><br /> <span data-ttu-id="74561-118">A atividade de <xref:System.Activities.Statements.FlowDecision> no final de <xref:System.Activities.Statements.Flowchart> avalia a propriedade de `currentState` para determinar se o estado é terminal.</span><span class="sxs-lookup"><span data-stu-id="74561-118">The <xref:System.Activities.Statements.FlowDecision> activity at the end of the <xref:System.Activities.Statements.Flowchart> evaluates the `currentState` property to determine whether the state is terminal.</span></span> <span data-ttu-id="74561-119">Se for, o fluxo de trabalho; termina se não controle de loop - voltar para o início da atividade de <xref:System.Activities.Statements.Pick> onde o fluxo de trabalho espera mais eventos do cronômetro.</span><span class="sxs-lookup"><span data-stu-id="74561-119">If it is, the workflow ends; otherwise control loops back to the start of the <xref:System.Activities.Statements.Pick> activity where the workflow waits for more stopwatch events.</span></span>|  
|<span data-ttu-id="74561-120">StopWatchClient</span><span class="sxs-lookup"><span data-stu-id="74561-120">StopWatchClient</span></span>|<span data-ttu-id="74561-121">Este é um aplicativo de console sequencial simples de fluxo de trabalho que envia vários eventos do cronômetro com enviar simples ou recebe combinações de atividade.</span><span class="sxs-lookup"><span data-stu-id="74561-121">This is a simple sequential workflow console application that sends various stopwatch events with simple Send or Receive activity combinations.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="74561-122">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="74561-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="74561-123">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], arquivo aberto de solução de StateMachineWithPick.sln.</span><span class="sxs-lookup"><span data-stu-id="74561-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open StateMachineWithPick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="74561-124">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="74561-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="74561-125">Iniciar o StopWatchService.exe de [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] como um administrador direito clicando o arquivo .exe e selecionando **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="74561-125">Start the StopWatchService.exe from [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] as an administrator by right clicking the .exe file and selecting **Run as administrator**.</span></span>  
  
    1.  <span data-ttu-id="74561-126">Navegue para o StateMachineWithPick CS StopWatchService \ \ \ bin \ debug.</span><span class="sxs-lookup"><span data-stu-id="74561-126">Navigate to the StateMachineWithPick\CS\StopWatchService\bin\Debug folder.</span></span>  
  
    2.  <span data-ttu-id="74561-127">O arquivo StopWatchService.exe e selecione **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="74561-127">Right-click the StopWatchService.exe file and select **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="74561-128">Inicie o aplicativo cliente de StopWatchClient de dentro de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74561-128">Start the StopWatchClient client application from within [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    1.  <span data-ttu-id="74561-129">Em **Solution Explorer**, selecione o **StopWatchClient** do projeto e clique **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="74561-129">In **Solution Explorer**, select the **StopWatchClient** project and right-click **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="74561-130">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="74561-130">To run the solution, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="74561-131">Alternar de volta para a janela do console para que o StopWatchService.exe exibe o estado transições.</span><span class="sxs-lookup"><span data-stu-id="74561-131">Switch back to the console window for the StopWatchService.exe to view the state transitions.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74561-132">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="74561-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="74561-133">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="74561-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="74561-134">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="74561-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="74561-135">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="74561-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`