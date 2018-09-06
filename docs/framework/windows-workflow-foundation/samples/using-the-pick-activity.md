---
title: Usando a atividade de picareta
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 193b60bff7b08c0de9a0957668483eb73be97274
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784667"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="760b9-102">Usando a atividade de picareta</span><span class="sxs-lookup"><span data-stu-id="760b9-102">Using the Pick Activity</span></span>
<span data-ttu-id="760b9-103">Este exemplo demonstra como usar a atividade de <xref:System.Activities.Statements.Pick> .</span><span class="sxs-lookup"><span data-stu-id="760b9-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>  
  
 <span data-ttu-id="760b9-104">A atividade de <xref:System.Activities.Statements.Pick> fornece a modelagem com base em eventos do controle.</span><span class="sxs-lookup"><span data-stu-id="760b9-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="760b9-105">Se comporta semelhante à declaração C# `switch` , que executa somente um dos ramificações na declaração de `switch` .</span><span class="sxs-lookup"><span data-stu-id="760b9-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="760b9-106">Diferentemente de instrução de `switch` em que uma ramificação é executado em com base em um valor, a atividade de <xref:System.Activities.Statements.Pick> executa uma ramificação com base em como uma atividade completa.</span><span class="sxs-lookup"><span data-stu-id="760b9-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>  
  
 <span data-ttu-id="760b9-107">Este exemplo solicita um usuário a digite seu nome no console em um período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="760b9-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="760b9-108">A atividade de <xref:System.Activities.Statements.Pick> no exemplo tem duas ramificações de que são executados com base na se o usuário digita em seu nome dentro de 5 segundos ou não.</span><span class="sxs-lookup"><span data-stu-id="760b9-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="760b9-109">Se o usuário digita em seu nome dentro de 5 segundos, o primeiro ramificação será executado, que contém uma atividade personalizado de `ReadLine` ; se não a outra ramificação é executado, que contém uma atividade de <xref:System.Activities.Statements.Delay> .</span><span class="sxs-lookup"><span data-stu-id="760b9-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="760b9-110">Uma vez que um nome de usuário é digitado no console, o nome de usuário é impresso no console.</span><span class="sxs-lookup"><span data-stu-id="760b9-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="760b9-111">Se uma entrada não é inserido em 5 segundos, a operação é esgotado.</span><span class="sxs-lookup"><span data-stu-id="760b9-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="760b9-112">Demonstra</span><span class="sxs-lookup"><span data-stu-id="760b9-112">Demonstrates</span></span>  
 <span data-ttu-id="760b9-113">atividade de<xref:System.Activities.Statements.Pick> .</span><span class="sxs-lookup"><span data-stu-id="760b9-113"><xref:System.Activities.Statements.Pick> activity.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="760b9-114">Discussão</span><span class="sxs-lookup"><span data-stu-id="760b9-114">Discussion</span></span>  
 <span data-ttu-id="760b9-115">O exemplo inclui um fluxo de trabalho do designer e fluxo de trabalho codificado.</span><span class="sxs-lookup"><span data-stu-id="760b9-115">The sample includes a Designer workflow and coded workflow.</span></span>  
  
 <span data-ttu-id="760b9-116">Fluxo de trabalho do designer</span><span class="sxs-lookup"><span data-stu-id="760b9-116">Designer Workflow</span></span>  
 <span data-ttu-id="760b9-117">A versão de designer exemplo demonstra como criar um fluxo de trabalho no designer.</span><span class="sxs-lookup"><span data-stu-id="760b9-117">The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="760b9-118">Os seguintes arquivos estão incluídos:</span><span class="sxs-lookup"><span data-stu-id="760b9-118">The following files are included:</span></span>  
  
-   <span data-ttu-id="760b9-119">Module.vb: Inclui a função de `Main` que executa o fluxo de trabalho de exemplo.</span><span class="sxs-lookup"><span data-stu-id="760b9-119">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="760b9-120">ReadString.cs: Uma atividade personalizado que lê algumas entradas de console.</span><span class="sxs-lookup"><span data-stu-id="760b9-120">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
-   <span data-ttu-id="760b9-121">Sequence1.xaml: Um fluxo de trabalho criado usando o designer que usa a picareta.</span><span class="sxs-lookup"><span data-stu-id="760b9-121">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>  
  
 <span data-ttu-id="760b9-122">Fluxo de trabalho codificado</span><span class="sxs-lookup"><span data-stu-id="760b9-122">Coded Workflow</span></span>  
 <span data-ttu-id="760b9-123">A versão codificado de exemplo demonstra como criar um fluxo de trabalho no designer.</span><span class="sxs-lookup"><span data-stu-id="760b9-123">The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="760b9-124">Os seguintes arquivos estão incluídos:</span><span class="sxs-lookup"><span data-stu-id="760b9-124">The following files are included:</span></span>  
  
-   <span data-ttu-id="760b9-125">Module.vb: Inclui a função de `Main` que executa o fluxo de trabalho de exemplo.</span><span class="sxs-lookup"><span data-stu-id="760b9-125">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="760b9-126">ReadString.cs: Uma atividade personalizado que lê algumas entradas de console.</span><span class="sxs-lookup"><span data-stu-id="760b9-126">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="760b9-127">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="760b9-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="760b9-128">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de Pick.sln.</span><span class="sxs-lookup"><span data-stu-id="760b9-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Pick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="760b9-129">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="760b9-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="760b9-130">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="760b9-130">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="760b9-131">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="760b9-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="760b9-132">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="760b9-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="760b9-133">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="760b9-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="760b9-134">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="760b9-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`