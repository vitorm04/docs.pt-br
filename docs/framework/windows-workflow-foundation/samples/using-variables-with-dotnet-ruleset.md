---
title: Usando variáveis com o.NET Framework 3.5 Ruleset
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 216136ba084505947b5ab3c985284d704cb5872f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a><span data-ttu-id="1177f-102">Usando variáveis com o.NET Framework 3.5 Ruleset</span><span class="sxs-lookup"><span data-stu-id="1177f-102">Using Variables with a .NET Framework 3.5 Ruleset</span></span>
<span data-ttu-id="1177f-103">Este exemplo demonstra como criar um fluxo de trabalho que usa a atividade de <xref:System.Activities.Statements.Interop> para integrar uma atividade personalizado escrito em [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] que use a diretiva e regras.</span><span class="sxs-lookup"><span data-stu-id="1177f-103">This sample demonstrates how to create a workflow that uses the <xref:System.Activities.Statements.Interop> activity to integrate a custom activity written in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] that uses policy and rules.</span></span> <span data-ttu-id="1177f-104">O fluxo de trabalho passar dados personalizado pela atividade variáveis de associação às propriedades de dependência exposta pela atividade personalizado.</span><span class="sxs-lookup"><span data-stu-id="1177f-104">The workflow passes data to the custom activity by binding variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="sample-walkthrough"></a><span data-ttu-id="1177f-105">Passo a passo de exemplo</span><span class="sxs-lookup"><span data-stu-id="1177f-105">Sample walkthrough</span></span>  
  
#### <a name="to-examine-travelrulelibrary"></a><span data-ttu-id="1177f-106">Para examinar TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="1177f-106">To examine TravelRuleLibrary</span></span>  
  
1.  <span data-ttu-id="1177f-107">Usando o Visual Studio, abra o arquivo de solução de InteropWith35RuleSet.sln.</span><span class="sxs-lookup"><span data-stu-id="1177f-107">Using Visual Studio, open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="1177f-108">Abra o TravelRuleSet.cs no designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1177f-108">Open the TravelRuleSet.cs in the workflow designer.</span></span>  
  
     <span data-ttu-id="1177f-109">Uma atividade sequencial personalizado que contém <xref:System.Workflow.Activities.PolicyActivity> é exibida.</span><span class="sxs-lookup"><span data-stu-id="1177f-109">A custom sequential activity that contains a <xref:System.Workflow.Activities.PolicyActivity> is displayed.</span></span>  
  
3.  <span data-ttu-id="1177f-110">Clique duas vezes na atividade de política de DiscountPolicy para examinar as regras.</span><span class="sxs-lookup"><span data-stu-id="1177f-110">Double-click the DiscountPolicy policy activity to examine the rules.</span></span>  
  
     <span data-ttu-id="1177f-111">Os PNF do editor das regras até mostram as regras.</span><span class="sxs-lookup"><span data-stu-id="1177f-111">The Rules editor pops up to show the rules.</span></span>  
  
4.  <span data-ttu-id="1177f-112">Clique com botão direito do `DiscountPolicy` e selecione o **Exibir código** permite que você examine o código ao lado de código c# para a atividade.</span><span class="sxs-lookup"><span data-stu-id="1177f-112">Right click the `DiscountPolicy` and select the **View Code** option to examine the code beside C# code for the activity.</span></span>  
  
     <span data-ttu-id="1177f-113">Observe a configuração da propriedade de dependência para `DiscountLevel`.</span><span class="sxs-lookup"><span data-stu-id="1177f-113">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="1177f-114">Isso é equivalente a argumentos em [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1177f-114">This is equivalent to arguments in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="1177f-115"> argumentos, consulte [variáveis e argumentos](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="1177f-115"> arguments, see [Variables and Arguments](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span></span>  
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="1177f-116">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="1177f-116">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="1177f-117">Este é um projeto sequencial de fluxo de trabalho que usa a atividade de <xref:System.Activities.Statements.Interop> para integrar com o conjunto de regra personalizada criado no projeto de `TravelRuleLibrary` .</span><span class="sxs-lookup"><span data-stu-id="1177f-117">This is a sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom Rule set created in the `TravelRuleLibrary` project.</span></span> <span data-ttu-id="1177f-118">As variáveis são criados na atividade de alto nível <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="1177f-118">Variables are created on the top level <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="1177f-119">A atividade de <xref:System.Activities.Statements.Interop> é usada para integrar-se a atividade de `TravelRuleSet` .</span><span class="sxs-lookup"><span data-stu-id="1177f-119">The <xref:System.Activities.Statements.Interop> activity is used to integrate with the `TravelRuleSet` activity.</span></span> <span data-ttu-id="1177f-120">Variáveis que são declarados em <xref:System.Activities.Statements.Sequence> são usados para associar a propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="1177f-120">The variables that are declared on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="1177f-121">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="1177f-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="1177f-122">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de InteropWith35RuleSet.sln.</span><span class="sxs-lookup"><span data-stu-id="1177f-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="1177f-123">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="1177f-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1177f-124">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="1177f-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1177f-125">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1177f-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1177f-126">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1177f-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1177f-127">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="1177f-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1177f-128">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1177f-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`