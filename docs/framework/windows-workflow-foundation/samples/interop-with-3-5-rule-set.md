---
title: Interoperabilidade com conjunto de regras 3,5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22ef1dd3d45e855306ed6c68b779751bec567990
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="interop-with-35-rule-set"></a><span data-ttu-id="964a7-102">Interoperabilidade com conjunto de regras 3,5</span><span class="sxs-lookup"><span data-stu-id="964a7-102">Interop with 3.5 Rule Set</span></span>
<span data-ttu-id="964a7-103">Este exemplo demonstra o uso do <xref:System.Activities.Statements.Interop> atividade integrar uma atividade personalizada no [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] usando <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` e regras.</span><span class="sxs-lookup"><span data-stu-id="964a7-103">This sample demonstrates the use of the <xref:System.Activities.Statements.Interop> activity to integrate with a custom activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] using <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` and rules.</span></span> <span data-ttu-id="964a7-104">Passar dados para a atividade personalizado associando variáveis de [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] às propriedades de dependência exposta pela atividade personalizado.</span><span class="sxs-lookup"><span data-stu-id="964a7-104">It passes data to the custom activity by binding [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="964a7-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="964a7-105">Requirements</span></span>  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a><span data-ttu-id="964a7-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="964a7-106">Demonstrates</span></span>  
 <span data-ttu-id="964a7-107"><xref:System.Activities.Statements.Interop>atividade, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` atividade em [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] com propriedades de dependência</span><span class="sxs-lookup"><span data-stu-id="964a7-107"><xref:System.Activities.Statements.Interop> activity, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] with dependency properties</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="964a7-108">Discussão</span><span class="sxs-lookup"><span data-stu-id="964a7-108">Discussion</span></span>  
 <span data-ttu-id="964a7-109">O exemplo demonstra um dos cenários de integração para integrar uma atividade de [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="964a7-109">The sample demonstrates one of the integration scenarios for integrating with a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] activity.</span></span> <span data-ttu-id="964a7-110">Este exemplo inclui uma [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] atividade personalizada que invoca um <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` atividade.</span><span class="sxs-lookup"><span data-stu-id="964a7-110">This sample includes a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] custom activity that invokes a <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity.</span></span>  
  
## <a name="travelrulelibrary"></a><span data-ttu-id="964a7-111">TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="964a7-111">TravelRuleLibrary</span></span>  
 <span data-ttu-id="964a7-112">Abrindo TravelRuleSet.cs no designer mostra uma atividade sequencial personalizado que contém uma atividade de política como segue</span><span class="sxs-lookup"><span data-stu-id="964a7-112">Opening TravelRuleSet.cs in the designer shows a custom sequential activity that contains a Policy activity as follows</span></span>  
  
 <span data-ttu-id="964a7-113">![Atividade de interoperabilidade](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span><span class="sxs-lookup"><span data-stu-id="964a7-113">![Interop Activity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span></span>  
  
 <span data-ttu-id="964a7-114">Clique duas vezes o **DiscountPolicy** atividade de política para examinar as regras.</span><span class="sxs-lookup"><span data-stu-id="964a7-114">Double-click the **DiscountPolicy** policy activity to examine the rules.</span></span> <span data-ttu-id="964a7-115">O editor das regras aparece para mostrar as regras.</span><span class="sxs-lookup"><span data-stu-id="964a7-115">The Rules editor appears to show the rules.</span></span>  
  
 <span data-ttu-id="964a7-116">![Editor de conjunto de regras](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span><span class="sxs-lookup"><span data-stu-id="964a7-116">![Rule Set Editor](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span></span>  
  
 <span data-ttu-id="964a7-117">Clique com botão direito do **DiscountPolicy** atividade e selecione o **Exibir código** opção para examinar ao lado do código c# código que acompanha esta atividade.</span><span class="sxs-lookup"><span data-stu-id="964a7-117">Right-click the **DiscountPolicy** activity and select the **View Code** option to examine the code-beside C# code that goes with this activity.</span></span> <span data-ttu-id="964a7-118">Observe a configuração da propriedade de dependência para `DiscountLevel`.</span><span class="sxs-lookup"><span data-stu-id="964a7-118">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="964a7-119">Isso é equivalente a <xref:System.Activities.Argument> em [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="964a7-119">This is equivalent to an <xref:System.Activities.Argument> in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span>  
  
```  
public static DependencyProperty DiscountLevelProperty = DependencyProperty.Register("DiscountLevel", typeof(int), typeof(TravelRuleSet));  
  
[DescriptionAttribute("DiscountLevel")]  
[CategoryAttribute("DiscountLevel Category")]  
[BrowsableAttribute(true)]  
[DesignerSerializationVisibilityAttribute(DesignerSerializationVisibility.Visible)]  
public int DiscountLevel  
{  
   get  
   {  
return ((int)base.GetValue(TravelRuleSet.DiscountLevelProperty)));  
   }  
   set  
   {  
base.SetValue(TravelRuleSet.DiscountLevelProperty, value);  
   }  
}  
```  
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="964a7-120">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="964a7-120">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="964a7-121">Este é um projeto de fluxo de trabalho sequencial de [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] que usa a atividade de <xref:System.Activities.Statements.Interop> para integrar com o conjunto de regra personalizada criado no projeto de TravelRuleLibrary.</span><span class="sxs-lookup"><span data-stu-id="964a7-121">This is a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom rule set created in the TravelRuleLibrary project.</span></span> <span data-ttu-id="964a7-122">As variáveis são criados em <xref:System.Activities.Statements.Sequence> de nível superior como segue.</span><span class="sxs-lookup"><span data-stu-id="964a7-122">Variables are created on the top-level <xref:System.Activities.Statements.Sequence> as follows.</span></span>  
  
 <span data-ttu-id="964a7-123">![Variáveis](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span><span class="sxs-lookup"><span data-stu-id="964a7-123">![Variables](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span></span>  
  
 <span data-ttu-id="964a7-124">![Gerenciador de soluções](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span><span class="sxs-lookup"><span data-stu-id="964a7-124">![Solution Explorer](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span></span>  
  
 <span data-ttu-id="964a7-125">Finalmente, a atividade de <xref:System.Activities.Statements.Interop> é usada para integrar com o TravelRuleSet.</span><span class="sxs-lookup"><span data-stu-id="964a7-125">Lastly, the <xref:System.Activities.Statements.Interop> activity is used to integrate with the TravelRuleSet.</span></span> <span data-ttu-id="964a7-126">Variáveis que foram declarados anteriores em <xref:System.Activities.Statements.Sequence> são usados para associar a propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="964a7-126">The variables that were declared earlier on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
 <span data-ttu-id="964a7-127">![Tipo de atividade](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span><span class="sxs-lookup"><span data-stu-id="964a7-127">![Activity Type](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span></span>  
  
 <span data-ttu-id="964a7-128">![Seta](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span><span class="sxs-lookup"><span data-stu-id="964a7-128">![Arrow](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span></span>  
  
 <span data-ttu-id="964a7-129">![Propriedades](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span><span class="sxs-lookup"><span data-stu-id="964a7-129">![Properties](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="964a7-130">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="964a7-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="964a7-131">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="964a7-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="964a7-132">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="964a7-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="964a7-133">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="964a7-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
