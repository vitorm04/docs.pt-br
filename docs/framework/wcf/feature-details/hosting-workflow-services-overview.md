---
title: "Visão geral de serviços de fluxo de trabalho de hospedagem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0f473de9f16203d1b47ac227a1614b972b09e2f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="386e9-102">Visão geral de serviços de fluxo de trabalho de hospedagem</span><span class="sxs-lookup"><span data-stu-id="386e9-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="386e9-103">Serviços de fluxo de trabalho devem ser hospedados para executar.</span><span class="sxs-lookup"><span data-stu-id="386e9-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="386e9-104">O <xref:System.ServiceModel.WorkflowServiceHost> é o host de fluxo de trabalho de caixa que dá suporte a várias instâncias, configuração e sistema de mensagens do WCF (embora os fluxos de trabalho não são necessários para usar o sistema de mensagens para ser hospedado).</span><span class="sxs-lookup"><span data-stu-id="386e9-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="386e9-105">Ele também se integra com persistência, acompanhamento e controle de instância por meio de um conjunto de comportamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="386e9-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="386e9-106">Assim como do WCF <xref:System.ServiceModel.ServiceHost>, o <xref:System.ServiceModel.WorkflowServiceHost> pode ser auto-hospedado em qualquer aplicativo .NET gerenciado ou hospedado na web (como um arquivo de .xamlx) no IIS / WAS.</span><span class="sxs-lookup"><span data-stu-id="386e9-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="386e9-107">Os tópicos nesta seção descrevem como hospedar um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="386e9-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="386e9-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="386e9-108">In This Section</span></span>  
 [<span data-ttu-id="386e9-109">Serviços de hospedagem de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="386e9-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="386e9-110">Descreve os serviços de hospedagem de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="386e9-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="386e9-111">Internos do Host de serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="386e9-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="386e9-112">Descreve como <xref:System.ServiceModel.WorkflowServiceHost> processa mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="386e9-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="386e9-113">Extensibilidade de Host do serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="386e9-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="386e9-114">Descreve como estender a funcionalidade do host do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="386e9-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="386e9-115">Ponto de extremidade de controle de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="386e9-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="386e9-116">Descreve como definir um ponto de extremidade que permite criar instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="386e9-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>  
  
 [<span data-ttu-id="386e9-117">Como: hospedar um fluxo de trabalho sem serviço no IIS</span><span class="sxs-lookup"><span data-stu-id="386e9-117">How to: Host a non-service workflow in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 <span data-ttu-id="386e9-118">Demonstra a hospedagem de um fluxo de trabalho que não é um serviço de fluxo de trabalho no IIS.</span><span class="sxs-lookup"><span data-stu-id="386e9-118">Demonstrates hosting a workflow that is not a workflow service in IIS.</span></span>  
  
 [<span data-ttu-id="386e9-119">Como: hospedar um serviço de fluxo de trabalho com o Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="386e9-119">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="386e9-120">Demonstra como hospedar um serviço de fluxo de trabalho existente no Windows Server App Fabric.</span><span class="sxs-lookup"><span data-stu-id="386e9-120">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="386e9-121">Configurando WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="386e9-121">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="386e9-122">Descreve como controlar a persistência, o controle de alterações, o comportamento de ociosidade e sem tratamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="386e9-122">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="386e9-123">Referência</span><span class="sxs-lookup"><span data-stu-id="386e9-123">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="386e9-124">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="386e9-124">Related Sections</span></span>  
 [<span data-ttu-id="386e9-125">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="386e9-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
