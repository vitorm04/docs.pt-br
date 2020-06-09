---
title: Serviços de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 7b05c766-f181-425d-9a3d-2a5e150c85f7
ms.openlocfilehash: c7a5c6245702497fcd75341b3ff7ba08dc190fa5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600121"
---
# <a name="workflow-services"></a><span data-ttu-id="4f977-102">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4f977-102">Workflow Services</span></span>
<span data-ttu-id="4f977-103">O [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] permite descrever completamente um serviço baseado em fluxo de trabalho de maneira declarativa em XAML.</span><span class="sxs-lookup"><span data-stu-id="4f977-103">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] allows you to fully describe a workflow-based service declaratively in XAML.</span></span> <span data-ttu-id="4f977-104">Você pode definir um fluxo de trabalho que implementa o serviço e descreve pontos de extremidade que o serviço expõe, tudo totalmente em XAML.</span><span class="sxs-lookup"><span data-stu-id="4f977-104">You can define a workflow that implements your service and describe endpoints the service exposes, all entirely in XAML.</span></span> <span data-ttu-id="4f977-105">Os tópicos desta seção descrevem, detalhadamente, o modelo de programação que oferece suporte a escrever serviços de maneira declarativa.</span><span class="sxs-lookup"><span data-stu-id="4f977-105">The topics in this section describe, in detail, the programming model that supports writing services declaratively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f977-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4f977-106">In This Section</span></span>  
 [<span data-ttu-id="4f977-107">Visão geral dos serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4f977-107">Workflow Services Overview</span></span>](workflow-services-overview.md)  
 <span data-ttu-id="4f977-108">Descreve os componentes envolvidos em criar e hospedar um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4f977-108">Describes the components involved in creating and hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="4f977-109">Atividades de mensagem</span><span class="sxs-lookup"><span data-stu-id="4f977-109">Messaging Activities</span></span>](messaging-activities.md)  
 <span data-ttu-id="4f977-110">Discute as atividades que permitem que os fluxos de trabalho enviem e recebam mensagens.</span><span class="sxs-lookup"><span data-stu-id="4f977-110">Discusses activities that allow workflows to send and receive messages.</span></span>  
  
 [<span data-ttu-id="4f977-111">Como criar um serviço de fluxo de trabalho com atividades de mensagens</span><span class="sxs-lookup"><span data-stu-id="4f977-111">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)  
 <span data-ttu-id="4f977-112">Descreve como usar as atividades de mensagem para criar um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4f977-112">Describes how to use messaging activities to create a workflow service.</span></span>  
  
 [<span data-ttu-id="4f977-113">Como acessar um serviço de um aplicativo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4f977-113">How To: Access a Service From a Workflow Application</span></span>](how-to-access-a-service-from-a-workflow-application.md)  
 <span data-ttu-id="4f977-114">Discute como chamar um serviço de um aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4f977-114">Discusses how to call a service from a workflow application.</span></span>  
  
 [<span data-ttu-id="4f977-115">Correlation</span><span class="sxs-lookup"><span data-stu-id="4f977-115">Correlation</span></span>](correlation.md)  
 <span data-ttu-id="4f977-116">Discute como a correlação mapeia mensagens entre si e para instâncias.</span><span class="sxs-lookup"><span data-stu-id="4f977-116">Discusses how correlation maps messages to each other and to instances.</span></span>  
  
 [<span data-ttu-id="4f977-117">Processamento de mensagem com problema</span><span class="sxs-lookup"><span data-stu-id="4f977-117">Out-of-Order Message Processing</span></span>](out-of-order-message-processing.md)  
 <span data-ttu-id="4f977-118">Descreve como configurar um serviço para aceitar mensagens fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="4f977-118">Describes configuring a service to accept out of order messages.</span></span>  
  
 [<span data-ttu-id="4f977-119">Desenvolvimento de serviço de fluxo de trabalho de primeiro contrato</span><span class="sxs-lookup"><span data-stu-id="4f977-119">Contract First Workflow Service Development</span></span>](../../windows-workflow-foundation/contract-first-workflow-service-development.md)  
 <span data-ttu-id="4f977-120">Descreve a criação de um serviço de fluxo de trabalho com base em um contrato de serviço existente.</span><span class="sxs-lookup"><span data-stu-id="4f977-120">Describes creating a workflow service based on an existing service contract.</span></span>  
  
 [<span data-ttu-id="4f977-121">Como criar um serviço de fluxo de trabalho que consome um contrato de serviço existente</span><span class="sxs-lookup"><span data-stu-id="4f977-121">How to: Create a workflow service that consumes an existing service contract</span></span>](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)  
 <span data-ttu-id="4f977-122">Fornece um exemplo passo a passo de como criar um serviço de fluxo de trabalho usando um contrato de serviço existente.</span><span class="sxs-lookup"><span data-stu-id="4f977-122">Provides a step-by-step example of creating a workflow service using an existing service contract.</span></span>  
  
 [<span data-ttu-id="4f977-123">Visão geral de serviços de fluxo de trabalho de hospedagem</span><span class="sxs-lookup"><span data-stu-id="4f977-123">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)  
 <span data-ttu-id="4f977-124">Descreve os aspectos diferentes de hospedar um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4f977-124">Describes the different aspects of hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="4f977-125">Utilizando contratos no fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4f977-125">Using Contracts in Workflow</span></span>](using-contracts-in-workflow.md)  
 <span data-ttu-id="4f977-126">Descreve os diferentes tipos de contratos e inferência do contrato.</span><span class="sxs-lookup"><span data-stu-id="4f977-126">Describes the different types of contracts and contract inference.</span></span>
