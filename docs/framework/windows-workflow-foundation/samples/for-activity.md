---
title: Para atividades
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e77800b21d671a0de0cab6f442919f50ce5ca51b
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="for-activity"></a><span data-ttu-id="cd595-102">Para atividades</span><span class="sxs-lookup"><span data-stu-id="cd595-102">For Activity</span></span>
<span data-ttu-id="cd595-103">Para o exemplo demonstra como criar uma atividade personalizado que herda de <xref:System.Activities.NativeActivity>, e usá-lo em um fluxo de trabalho para executar um exemplo do mundo real.</span><span class="sxs-lookup"><span data-stu-id="cd595-103">The For sample demonstrates how to build a custom activity that inherits from <xref:System.Activities.NativeActivity>, and use it in a workflow to execute a real world example.</span></span> <span data-ttu-id="cd595-104">A atividade personalizado incluída nas funções deste exemplo desejar da declaração C# `for` .</span><span class="sxs-lookup"><span data-stu-id="cd595-104">The custom activity included in this sample functions like the C# `for` statement.</span></span> <span data-ttu-id="cd595-105">T</span><span class="sxs-lookup"><span data-stu-id="cd595-105">T</span></span>  
  
 <span data-ttu-id="cd595-106">A atividade personalizado de `For` tem propriedades chamadas `InitAction`, `IterationAction`, `Condition`, e `Body` que correspondem à declaração de inicialização, a instrução iterativa, a condição de continuação de linha, e a declaração do corpo respectivamente localizada na instrução padrão de C# `For` .</span><span class="sxs-lookup"><span data-stu-id="cd595-106">The `For` custom activity has properties named `InitAction`, `IterationAction`, `Condition`, and `Body` that correspond to the initialization statement, iterative statement, continuation condition, and body statement respectively found in the standard C# `For` statement.</span></span>  
  
 <span data-ttu-id="cd595-107">A tabela a seguir descreve os arquivos de chave no exemplo.</span><span class="sxs-lookup"><span data-stu-id="cd595-107">The following table describes the key files in the sample.</span></span>  
  
|<span data-ttu-id="cd595-108">Arquivo</span><span class="sxs-lookup"><span data-stu-id="cd595-108">File</span></span>|<span data-ttu-id="cd595-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd595-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cd595-110">For.cs</span><span class="sxs-lookup"><span data-stu-id="cd595-110">For.cs</span></span>|<span data-ttu-id="cd595-111">Definição de classe para atividades personalizado de `For` , que estende a classe de <xref:System.Activities.NativeActivity> para fornecer funcionalidade da declaração C# `For` .</span><span class="sxs-lookup"><span data-stu-id="cd595-111">Class definition for the `For` custom activity, which extends the <xref:System.Activities.NativeActivity> class to provide the functionality of the C# `For` statement.</span></span>|  
|<span data-ttu-id="cd595-112">Module.vb</span><span class="sxs-lookup"><span data-stu-id="cd595-112">Program.cs</span></span>|<span data-ttu-id="cd595-113">Um aplicativo cliente que executa o trabalho iterativo básico em uma coleção usando a atividade personalizado de `For` .</span><span class="sxs-lookup"><span data-stu-id="cd595-113">A client application that performs basic iterative work on a collection using the custom `For` activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="cd595-114">Ao usar a atividade de `For` personalizado, certifique-se de que a propriedade de `Condition` é definida; se não um loop infinito pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="cd595-114">When using the `For` custom activity, ensure that the `Condition` property is set; otherwise an infinite loop could occur.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="cd595-115">Demonstra</span><span class="sxs-lookup"><span data-stu-id="cd595-115">Demonstrates</span></span>  
 <span data-ttu-id="cd595-116">Crie uma atividade personalizado que herda de <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="cd595-116">Create a custom activity that inherits from <xref:System.Activities.NativeActivity>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="cd595-117">Discussão</span><span class="sxs-lookup"><span data-stu-id="cd595-117">Discussion</span></span>  
 <span data-ttu-id="cd595-118">A tabela a seguir descreve as propriedades de atividade incluída neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="cd595-118">The following table describes the properties of the activity included in this sample.</span></span>  
  
 <span data-ttu-id="cd595-119">InitAction</span><span class="sxs-lookup"><span data-stu-id="cd595-119">InitAction</span></span>  
 <span data-ttu-id="cd595-120">Declaração de inicialização</span><span class="sxs-lookup"><span data-stu-id="cd595-120">Initialization statement</span></span>  
  
 <span data-ttu-id="cd595-121">IterationAction</span><span class="sxs-lookup"><span data-stu-id="cd595-121">IterationAction</span></span>  
 <span data-ttu-id="cd595-122">Instrução iterativa</span><span class="sxs-lookup"><span data-stu-id="cd595-122">Iterative statement</span></span>  
  
 <span data-ttu-id="cd595-123">Condição</span><span class="sxs-lookup"><span data-stu-id="cd595-123">Condition</span></span>  
 <span data-ttu-id="cd595-124">Declaração de continuação de linha</span><span class="sxs-lookup"><span data-stu-id="cd595-124">Continuation statement</span></span>  
  
 <span data-ttu-id="cd595-125">Corpo</span><span class="sxs-lookup"><span data-stu-id="cd595-125">Body</span></span>  
 <span data-ttu-id="cd595-126">Instrução do corpo</span><span class="sxs-lookup"><span data-stu-id="cd595-126">Body statement</span></span>  
  
 <span data-ttu-id="cd595-127">A atividade herda de <xref:System.Activities.NativeActivity> para conceder acesso aos recursos de tempo de execução como agendar atividades adicionais para executar, usando um dos métodos de `ScheduleActivity` de <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="cd595-127">The activity inherits from <xref:System.Activities.NativeActivity> to gain access to runtime features such as scheduling additional activities to run, using one of the `ScheduleActivity` methods of <xref:System.Activities.NativeActivityContext>.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="cd595-128">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="cd595-128">To use this sample</span></span>  
  
1.  <span data-ttu-id="cd595-129">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de For.sln.</span><span class="sxs-lookup"><span data-stu-id="cd595-129">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the For.sln solution file.</span></span>  
  
2.  <span data-ttu-id="cd595-130">Crie a solução, pressionando CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="cd595-130">Build the solution, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="cd595-131">Executar a solução, pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="cd595-131">Run the solution, by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cd595-132">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cd595-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cd595-133">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cd595-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cd595-134">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="cd595-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cd595-135">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cd595-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`