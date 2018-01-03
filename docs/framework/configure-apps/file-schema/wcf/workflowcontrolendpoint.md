---
title: '&lt;workflowControlEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 443d23a3b0f73d2fd0a08112d51f745d1e1874fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="2a5e9-102">&lt;workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="2a5e9-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="2a5e9-103">Este elemento de configuração define um ponto de extremidade padrão para controlar a execução de instâncias de fluxo de trabalho (criar, executar, suspender, terminar, etc).</span><span class="sxs-lookup"><span data-stu-id="2a5e9-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="2a5e9-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2a5e9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a5e9-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2a5e9-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a5e9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a5e9-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a5e9-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2a5e9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2a5e9-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2a5e9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a5e9-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a5e9-109">Attributes</span></span>  
  
|<span data-ttu-id="2a5e9-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="2a5e9-110">Attribute</span></span>|<span data-ttu-id="2a5e9-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a5e9-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a5e9-112">name</span><span class="sxs-lookup"><span data-stu-id="2a5e9-112">name</span></span>|<span data-ttu-id="2a5e9-113">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="2a5e9-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="2a5e9-114">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="2a5e9-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a5e9-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2a5e9-115">Child Elements</span></span>  
 <span data-ttu-id="2a5e9-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2a5e9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a5e9-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a5e9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2a5e9-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a5e9-118">Element</span></span>|<span data-ttu-id="2a5e9-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a5e9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a5e9-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2a5e9-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="2a5e9-121">Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="2a5e9-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a5e9-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a5e9-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
