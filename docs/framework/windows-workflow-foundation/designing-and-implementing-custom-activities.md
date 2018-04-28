---
title: Criando e implementando atividades personalizadas
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bafa54764ba8b02dd05cadd65c3f3cbc64c4b081
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="bc0c9-102">Criando e implementando atividades personalizadas</span><span class="sxs-lookup"><span data-stu-id="bc0c9-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="bc0c9-103">As atividades personalizadas no [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] são criadas montando atividades fornecida pelo sistema em atividades compostas ou criando novos tipos que derivam de <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> ou <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="bc0c9-104">Esta seção descreve como criar atividades personalizadas com um dos métodos.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc0c9-105">Atividades personalizadas por padrão são exibidas no designer de fluxo de trabalho como um retângulo simples com o nome da atividade.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="bc0c9-106">Para fornecer uma representação visual de sua atividade personalizada no designer de fluxo de trabalho, você também deverá criar um designer personalizado.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="bc0c9-107">Para obter mais informações, consulte [modelos e Designers de atividade personalizada usando](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="bc0c9-107">For more information, see [Using Custom Activity Designers and Templates](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc0c9-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="bc0c9-108">In This Section</span></span>  
 [<span data-ttu-id="bc0c9-109">Opções de criação de atividades</span><span class="sxs-lookup"><span data-stu-id="bc0c9-109">Activity Authoring Options</span></span>](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 <span data-ttu-id="bc0c9-110">Discute os estilos de criação disponíveis no [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bc0c9-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="bc0c9-111">Usando uma atividade personalizada</span><span class="sxs-lookup"><span data-stu-id="bc0c9-111">Using a custom activity</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 <span data-ttu-id="bc0c9-112">Descreve como adicionar uma atividade personalizada a um projeto do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="bc0c9-113">Criando atividades assíncronas</span><span class="sxs-lookup"><span data-stu-id="bc0c9-113">Creating Asynchronous Activities</span></span>](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="bc0c9-114">Descreve como criar atividades assíncronas.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="bc0c9-115">Configurando a atividade de validação</span><span class="sxs-lookup"><span data-stu-id="bc0c9-115">Configuring Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 <span data-ttu-id="bc0c9-116">Descreve como a validação de atividade pode ser usada para identificar e relatar erros na configuração de uma atividade antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="bc0c9-117">Criando uma atividade em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bc0c9-117">Creating an Activity at Runtime</span></span>](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="bc0c9-118">Discute como criar atividades em tempo de execução usando <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="bc0c9-119">Propriedades de execução de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="bc0c9-119">Workflow Execution Properties</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 <span data-ttu-id="bc0c9-120">Descreve como usar as propriedades de execução do fluxo de trabalho para adicionar propriedades específicas de contexto ao ambiente de uma atividade</span><span class="sxs-lookup"><span data-stu-id="bc0c9-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="bc0c9-121">Usando representantes de atividades</span><span class="sxs-lookup"><span data-stu-id="bc0c9-121">Using Activity Delegates</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 <span data-ttu-id="bc0c9-122">Discute como criar e usar as atividades que contêm representantes de atividade.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-122">Discusses how to author and use activities that contain activity delegates.</span></span>  
  
 [<span data-ttu-id="bc0c9-123">Localização de atividades</span><span class="sxs-lookup"><span data-stu-id="bc0c9-123">Activity Localization</span></span>](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 <span data-ttu-id="bc0c9-124">Descreve como usar a localização de recursos de cadeia de caracteres em atividades.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-124">Describes how to use localization of string resources in activities.</span></span>  
  
 [<span data-ttu-id="bc0c9-125">Usando extensões de atividade</span><span class="sxs-lookup"><span data-stu-id="bc0c9-125">Using Activity Extensions</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 <span data-ttu-id="bc0c9-126">Descreve como criar e usar extensões de atividade.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-126">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="bc0c9-127">Consumindo feeds do OData de um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="bc0c9-127">Consuming OData Feeds from a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="bc0c9-128">Descreve vários métodos para chamar um WCF Data Service de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-128">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="bc0c9-129">Escopo e visibilidade de definição de atividades</span><span class="sxs-lookup"><span data-stu-id="bc0c9-129">Activity Definition Scoping and Visibility</span></span>](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="bc0c9-130">Descreve as opções e as regras para definir o escopo de dados e a visibilidade de membros para atividades.</span><span class="sxs-lookup"><span data-stu-id="bc0c9-130">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
