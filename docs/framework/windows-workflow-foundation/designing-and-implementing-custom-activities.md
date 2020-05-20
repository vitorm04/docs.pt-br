---
title: Criando e implementando atividades personalizadas
description: Este artigo fornece recursos para a criação de atividades personalizadas no Workflow Foundation criando atividades compostas ou criando novos tipos de atividade.
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 9c184bff9518bb5581f3bf4cd408db224736192b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419987"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="545af-103">Criando e implementando atividades personalizadas</span><span class="sxs-lookup"><span data-stu-id="545af-103">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="545af-104">As atividades personalizadas no [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] são criadas montando atividades fornecida pelo sistema em atividades compostas ou criando novos tipos que derivam de <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> ou <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="545af-104">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="545af-105">Esta seção descreve como criar atividades personalizadas com um dos métodos.</span><span class="sxs-lookup"><span data-stu-id="545af-105">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="545af-106">Atividades personalizadas por padrão são exibidas no designer de fluxo de trabalho como um retângulo simples com o nome da atividade.</span><span class="sxs-lookup"><span data-stu-id="545af-106">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="545af-107">Para fornecer uma representação visual de sua atividade personalizada no designer de fluxo de trabalho, você também deverá criar um designer personalizado.</span><span class="sxs-lookup"><span data-stu-id="545af-107">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="545af-108">Para obter mais informações, consulte [usando modelos e designers de atividades personalizados](using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="545af-108">For more information, see [Using Custom Activity Designers and Templates](using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="545af-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="545af-109">In This Section</span></span>  
 [<span data-ttu-id="545af-110">Opções de criação de atividades</span><span class="sxs-lookup"><span data-stu-id="545af-110">Activity Authoring Options</span></span>](activity-authoring-options-in-wf.md)  
 <span data-ttu-id="545af-111">Discute os estilos de criação disponíveis no [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="545af-111">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="545af-112">Usando uma atividade personalizada</span><span class="sxs-lookup"><span data-stu-id="545af-112">Using a custom activity</span></span>](using-a-custom-activity.md)  
 <span data-ttu-id="545af-113">Descreve como adicionar uma atividade personalizada a um projeto do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="545af-113">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="545af-114">Criando atividades assíncronas</span><span class="sxs-lookup"><span data-stu-id="545af-114">Creating Asynchronous Activities</span></span>](creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="545af-115">Descreve como criar atividades assíncronas.</span><span class="sxs-lookup"><span data-stu-id="545af-115">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="545af-116">Configurando a atividade de validação</span><span class="sxs-lookup"><span data-stu-id="545af-116">Configuring Activity Validation</span></span>](configuring-activity-validation.md)  
 <span data-ttu-id="545af-117">Descreve como a validação de atividade pode ser usada para identificar e relatar erros na configuração de uma atividade antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="545af-117">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="545af-118">Criando uma atividade em runtime</span><span class="sxs-lookup"><span data-stu-id="545af-118">Creating an Activity at Runtime</span></span>](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="545af-119">Discute como criar atividades em runtime usando <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="545af-119">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="545af-120">Propriedades de execução de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="545af-120">Workflow Execution Properties</span></span>](workflow-execution-properties.md)  
 <span data-ttu-id="545af-121">Descreve como usar as propriedades de execução do fluxo de trabalho para adicionar propriedades específicas de contexto ao ambiente de uma atividade</span><span class="sxs-lookup"><span data-stu-id="545af-121">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="545af-122">Usando representantes de atividades</span><span class="sxs-lookup"><span data-stu-id="545af-122">Using Activity Delegates</span></span>](using-activity-delegates.md)  
 <span data-ttu-id="545af-123">Discute como criar e usar as atividades que contêm representantes de atividade.</span><span class="sxs-lookup"><span data-stu-id="545af-123">Discusses how to author and use activities that contain activity delegates.</span></span>
  
 [<span data-ttu-id="545af-124">Usando extensões de atividade</span><span class="sxs-lookup"><span data-stu-id="545af-124">Using Activity Extensions</span></span>](using-activity-extensions.md)  
 <span data-ttu-id="545af-125">Descreve como criar e usar extensões de atividade.</span><span class="sxs-lookup"><span data-stu-id="545af-125">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="545af-126">Consumindo feeds do OData de um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="545af-126">Consuming OData Feeds from a Workflow</span></span>](consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="545af-127">Descreve vários métodos para chamar um WCF Data Service de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="545af-127">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="545af-128">Escopo e visibilidade de definição de atividades</span><span class="sxs-lookup"><span data-stu-id="545af-128">Activity Definition Scoping and Visibility</span></span>](activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="545af-129">Descreve as opções e as regras para definir o escopo de dados e a visibilidade de membros para atividades.</span><span class="sxs-lookup"><span data-stu-id="545af-129">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
