---
title: "Orientação de migração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e04c63754960dca44558d888b8ce357220562ea7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="migration-guidance"></a><span data-ttu-id="56925-102">Orientação de migração</span><span class="sxs-lookup"><span data-stu-id="56925-102">Migration Guidance</span></span>
<span data-ttu-id="56925-103">No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], a Microsoft está liberando a segunda versão principal do [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56925-103">In the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], Microsoft is releasing the second major version of [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="56925-104">O [!INCLUDE[wf1](../../../includes/wf1-md.md)] foi liberado no [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (isso inclui os tipos nos namespaces System.Workflow.\*; agora referido como WF3) e aprimorado no [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56925-104">[!INCLUDE[wf1](../../../includes/wf1-md.md)] was released in [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (this included the types in the System.Workflow.\* namespaces; now referred to as WF3) and enhanced in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="56925-105">WF3 também é parte do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], mas ele não houver junto com a nova tecnologia de fluxo de trabalho (os tipos em System. Activities.\* namespaces; conhecido como WF4).</span><span class="sxs-lookup"><span data-stu-id="56925-105">WF3 is also part of the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], but it exists there alongside new workflow technology (the types in the System.Activities.\* namespaces; referred to as WF4).</span></span> <span data-ttu-id="56925-106">Ao considerar quando adotar o WF4, é importante primeiro reconhecer que você controla o tempo.</span><span class="sxs-lookup"><span data-stu-id="56925-106">When considering when to adopt WF4, it is important to first recognize that you control the timing.</span></span>  
  
-   <span data-ttu-id="56925-107">O WF3 tem suporte completo do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56925-107">WF3 is a fully supported part of the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span>  
  
-   <span data-ttu-id="56925-108">Os aplicativos WF3 são executados no [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] sem alteração e continua tendo suporte total.</span><span class="sxs-lookup"><span data-stu-id="56925-108">WF3 applications run on the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] without modification and continue to be fully supported.</span></span>  
  
-   <span data-ttu-id="56925-109">Os novos aplicativos WF3 podem ser criados e seus aplicativos existentes podem ser editados no [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] e têm suporte total.</span><span class="sxs-lookup"><span data-stu-id="56925-109">New WF3 applications can be created and your existing applications can be edited in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and are fully supported.</span></span>  
  
 <span data-ttu-id="56925-110">Portanto, a decisão de adotar o .NET Framework 4 é separada da sua decisão de mover para o WF4 (System.Activities.*) de WF3 (System.\*).</span><span class="sxs-lookup"><span data-stu-id="56925-110">Thus, the decision to adopt the .NET Framework 4 is decoupled from your decision to move to WF4 (System.Activities.*) from WF3 (System.Workflow.\*).</span></span> <span data-ttu-id="56925-111">Este tópico fornece links para a orientação de migração do WF que fornece informações sobre como trabalhar com WF3 e WF4.</span><span class="sxs-lookup"><span data-stu-id="56925-111">This topic provides links to WF migration guidance that provides information about working with WF3 and WF4.</span></span>  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a><span data-ttu-id="56925-112">Artigos e livros de receitas de migração do WF</span><span class="sxs-lookup"><span data-stu-id="56925-112">WF Migration Whitepapers and Cookbooks</span></span>  
 <span data-ttu-id="56925-113">O [visão geral da migração WF](http://go.microsoft.com/fwlink/?LinkId=153873) tópico fornece uma visão geral da relação entre as estratégias de WF3 e WF4 e migração.</span><span class="sxs-lookup"><span data-stu-id="56925-113">The [WF Migration Overview](http://go.microsoft.com/fwlink/?LinkId=153873) topic provides a broad overview of the relationship between WF3 and WF4 and migration strategies.</span></span> <span data-ttu-id="56925-114">Os tópicos complementares aprofundam tópicos específicos.</span><span class="sxs-lookup"><span data-stu-id="56925-114">Companion topics drill into specific topics.</span></span>  
  
 [<span data-ttu-id="56925-115">Visão geral da migração WF</span><span class="sxs-lookup"><span data-stu-id="56925-115">WF Migration Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=153873)  
 <span data-ttu-id="56925-116">Descreve a relação entre WF3 e WF4, e as opções que você tem como usuário ou usuário potencial da tecnologia de fluxo de trabalho no .NET 4.</span><span class="sxs-lookup"><span data-stu-id="56925-116">Describes the relationship between WF3 and WF4, and the choices you have as a user or a potential user of workflow technology in .NET 4.</span></span>  
  
 [<span data-ttu-id="56925-117">Migração WF: Práticas recomendadas para o desenvolvimento de WF3</span><span class="sxs-lookup"><span data-stu-id="56925-117">WF Migration: Best Practices for WF3 Development</span></span>](http://go.microsoft.com/fwlink/?LinkId=153852)  
 <span data-ttu-id="56925-118">Discute como criar os artefatos do WF3 para que eles possam ser migrados mais facilmente para o WF4.</span><span class="sxs-lookup"><span data-stu-id="56925-118">Discusses how to design WF3 artifacts so they can be more easily migrated to WF4.</span></span>  
  
 [<span data-ttu-id="56925-119">Diretrizes de WF: regras</span><span class="sxs-lookup"><span data-stu-id="56925-119">WF Guidance: Rules</span></span>](http://go.microsoft.com/fwlink/?LinkId=153854)  
 <span data-ttu-id="56925-120">Discute como transformar investimentos relacionadas a regras em soluções do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56925-120">Discusses how to bring rules-related investments forward into [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] solutions.</span></span>  
  
 [<span data-ttu-id="56925-121">WF diretrizes: Máquina de estado</span><span class="sxs-lookup"><span data-stu-id="56925-121">WF Guidance: State Machine</span></span>](http://go.microsoft.com/fwlink/?LinkId=153855)  
 <span data-ttu-id="56925-122">Discute a modelagem do fluxo de controle do WF4 na ausência de uma atividade da máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="56925-122">Discusses WF4 control flow modeling in the absence of a State-Machine activity.</span></span>  
  
 <span data-ttu-id="56925-123">Observe que essa orientação somente se aplica a projetos de fluxo de trabalho destinados ao .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="56925-123">Note that this guidance only applies to workflow projects that target .NET Framework 4.</span></span> <span data-ttu-id="56925-124">Os fluxos de trabalho da máquina de estado eram adicionados no .NET 4.0.1 com a versão de atualização 1 da plataforma, e foram incluídos como parte do .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="56925-124">State Machine workflows were added in .NET 4.0.1 with the release of Platform Update 1, and were included as part of .NET Framework 4.5.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="56925-125">fluxos de trabalho de máquina de estado no .NET 4.0.1 - 4.0.3 e o .NET Framework 4.5, consulte [atualização 4.0.1 para Microsoft .NET Framework 4 recursos](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) e [fluxos de trabalho de máquina de estado](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="56925-125"> state machine workflows in .NET 4.0.1 - 4.0.3 and .NET Framework 4.5, see [Update 4.0.1 for Microsoft .NET Framework 4 Features](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) and [State Machine Workflows](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).</span></span>  
  
 [<span data-ttu-id="56925-126">WF livro de receitas de migração: Atividades personalizadas</span><span class="sxs-lookup"><span data-stu-id="56925-126">WF Migration Cookbook: Custom Activities</span></span>](http://go.microsoft.com/fwlink/?LinkId=153856)  
 <span data-ttu-id="56925-127">Fornece exemplos e instruções para recriar as atividades personalizadas do WF3 no WF4.</span><span class="sxs-lookup"><span data-stu-id="56925-127">Provides examples and instructions for redesigning WF3 custom activities on WF4.</span></span>  
  
 [<span data-ttu-id="56925-128">Guia de migração de WF: Avançado de atividades personalizadas</span><span class="sxs-lookup"><span data-stu-id="56925-128">WF Migration Cookbook: Advanced Custom Activities</span></span>](http://go.microsoft.com/fwlink/?LinkId=275560)  
 <span data-ttu-id="56925-129">Fornece orientação para reformatar as atividades personalizadas avançadas do WF3 que usam filas do WF3 e agendar atividades filho como atividades personalizadas do WF4.</span><span class="sxs-lookup"><span data-stu-id="56925-129">Provides guidance for redesigning advanced WF3 custom activities that use WF3 queues and schedule child activities as WF4 custom activities.</span></span>  
  
 [<span data-ttu-id="56925-130">Guia de migração de WF: fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="56925-130">WF Migration Cookbook: Workflows</span></span>](http://go.microsoft.com/fwlink/?LinkId=153858)  
 <span data-ttu-id="56925-131">Fornece exemplos e instruções para recriar os fluxos de trabalho do WF3 no WF4.</span><span class="sxs-lookup"><span data-stu-id="56925-131">Provides examples and instructions for redesigning WF3 workflows on WF4.</span></span>  
  
 [<span data-ttu-id="56925-132">WF livro de receitas de migração: Hospedagem de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="56925-132">WF Migration Cookbook: Workflow Hosting</span></span>](http://go.microsoft.com/fwlink/?LinkId=275561)  
 <span data-ttu-id="56925-133">Fornece orientação para reformatar o código de hospedagem do WF3 como código de hospedagem do WF4.</span><span class="sxs-lookup"><span data-stu-id="56925-133">Provides guidance for redesigning WF3 hosting code as WF4 hosting code.</span></span> <span data-ttu-id="56925-134">A meta é abranger as principais diferenças na hospedagem de fluxo de trabalho entre WF3 e WF4.</span><span class="sxs-lookup"><span data-stu-id="56925-134">The goal is to cover the key differences in workflow hosting between WF3 and WF4.</span></span>  
  
 [<span data-ttu-id="56925-135">WF livro de receitas de migração: Controle de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="56925-135">WF Migration Cookbook: Workflow Tracking</span></span>](http://go.microsoft.com/fwlink/?LinkId=275562)  
 <span data-ttu-id="56925-136">Fornece orientação para reformatar o código de rastreamento e a configuração do WF3 usando o código de rastreamento e a configuração equivalentes do WF4.</span><span class="sxs-lookup"><span data-stu-id="56925-136">Provides guidance for redesigning WF3 tracking code and configuration using equivalent WF4 tracking code and configuration.</span></span>  
  
 [<span data-ttu-id="56925-137">WF diretrizes: Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="56925-137">WF Guidance: Workflow Services</span></span>](http://go.microsoft.com/fwlink/?LinkId=275564)  
 <span data-ttu-id="56925-138">Fornece instruções passo a passo orientadas para exemplos para recriar os fluxos de trabalho que implementam os serviços Web do Windows Communication Foundation (WCF) (geralmente chamado de serviços de fluxo de trabalho) criados no WF3 para usar WF4, para cenários comuns para atividades prontas.</span><span class="sxs-lookup"><span data-stu-id="56925-138">Provides example-oriented step-by-step instructions for redesigning workflows that implement Windows Communication Foundation (WCF) web services (commonly referred to as workflow services) created in WF3 to use WF4, for common scenarios for out-of-box activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56925-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56925-139">See Also</span></span>  
 <xref:System.Activities.Statements.Interop>
