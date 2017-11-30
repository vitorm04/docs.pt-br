---
title: Usando a atividade de picareta
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 85b7e3b02efbf6ebe2b604cbeb24f00c2721948a
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="4a4e0-102">Usando a atividade de picareta</span><span class="sxs-lookup"><span data-stu-id="4a4e0-102">Using the Pick Activity</span></span>
<span data-ttu-id="4a4e0-103">Este exemplo demonstra como usar a atividade de <xref:System.Activities.Statements.Pick> .</span><span class="sxs-lookup"><span data-stu-id="4a4e0-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>  
  
 <span data-ttu-id="4a4e0-104">A atividade de <xref:System.Activities.Statements.Pick> fornece a modelagem com base em eventos do controle.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="4a4e0-105">Se comporta semelhante à declaração C# `switch` , que executa somente um dos ramificações na declaração de `switch` .</span><span class="sxs-lookup"><span data-stu-id="4a4e0-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="4a4e0-106">Diferentemente de instrução de `switch` em que uma ramificação é executado em com base em um valor, a atividade de <xref:System.Activities.Statements.Pick> executa uma ramificação com base em como uma atividade completa.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>  
  
 <span data-ttu-id="4a4e0-107">Este exemplo solicita um usuário a digite seu nome no console em um período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="4a4e0-108">A atividade de <xref:System.Activities.Statements.Pick> no exemplo tem duas ramificações de que são executados com base na se o usuário digita em seu nome dentro de 5 segundos ou não.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="4a4e0-109">Se o usuário digita em seu nome dentro de 5 segundos, o primeiro ramificação será executado, que contém uma atividade personalizado de `ReadLine` ; se não a outra ramificação é executado, que contém uma atividade de <xref:System.Activities.Statements.Delay> .</span><span class="sxs-lookup"><span data-stu-id="4a4e0-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="4a4e0-110">Uma vez que um nome de usuário é digitado no console, o nome de usuário é impresso no console.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="4a4e0-111">Se uma entrada não é inserido em 5 segundos, a operação é esgotado.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4a4e0-112">Demonstra</span><span class="sxs-lookup"><span data-stu-id="4a4e0-112">Demonstrates</span></span>  
 <span data-ttu-id="4a4e0-113">atividade de<xref:System.Activities.Statements.Pick> .</span><span class="sxs-lookup"><span data-stu-id="4a4e0-113"><xref:System.Activities.Statements.Pick> activity.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4a4e0-114">Discussão</span><span class="sxs-lookup"><span data-stu-id="4a4e0-114">Discussion</span></span>  
 <span data-ttu-id="4a4e0-115">O exemplo inclui um fluxo de trabalho do designer e fluxo de trabalho codificado.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-115">The sample includes a Designer workflow and coded workflow.</span></span>  
  
 <span data-ttu-id="4a4e0-116">Fluxo de trabalho do designer</span><span class="sxs-lookup"><span data-stu-id="4a4e0-116">Designer Workflow</span></span>  
 <span data-ttu-id="4a4e0-117">A versão de designer exemplo demonstra como criar um fluxo de trabalho no designer.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-117">The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="4a4e0-118">Os seguintes arquivos estão incluídos:</span><span class="sxs-lookup"><span data-stu-id="4a4e0-118">The following files are included:</span></span>  
  
-   <span data-ttu-id="4a4e0-119">Module.vb: Inclui a função de `Main` que executa o fluxo de trabalho de exemplo.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-119">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="4a4e0-120">ReadString.cs: Uma atividade personalizado que lê algumas entradas de console.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-120">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
-   <span data-ttu-id="4a4e0-121">Sequence1.xaml: Um fluxo de trabalho criado usando o designer que usa a picareta.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-121">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>  
  
 <span data-ttu-id="4a4e0-122">Fluxo de trabalho codificado</span><span class="sxs-lookup"><span data-stu-id="4a4e0-122">Coded Workflow</span></span>  
 <span data-ttu-id="4a4e0-123">A versão codificado de exemplo demonstra como criar um fluxo de trabalho no designer.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-123">The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="4a4e0-124">Os seguintes arquivos estão incluídos:</span><span class="sxs-lookup"><span data-stu-id="4a4e0-124">The following files are included:</span></span>  
  
-   <span data-ttu-id="4a4e0-125">Module.vb: Inclui a função de `Main` que executa o fluxo de trabalho de exemplo.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-125">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="4a4e0-126">ReadString.cs: Uma atividade personalizado que lê algumas entradas de console.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-126">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4a4e0-127">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="4a4e0-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="4a4e0-128">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de Pick.sln.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Pick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="4a4e0-129">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4a4e0-130">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-130">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4a4e0-131">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4a4e0-132">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4a4e0-133">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4a4e0-134">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4a4e0-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`