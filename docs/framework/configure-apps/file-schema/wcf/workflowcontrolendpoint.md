---
title: '&lt;WorkflowControlEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 87c745cfb8f7cd98c25cd34fc1aa94a26a5ba507
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="471e7-102">&lt;WorkflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="471e7-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="471e7-103">Este elemento de configuração define um ponto de extremidade padrão para controlar a execução de instâncias de fluxo de trabalho (criar, executar, suspender, terminar, etc).</span><span class="sxs-lookup"><span data-stu-id="471e7-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="471e7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="471e7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="471e7-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="471e7-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="471e7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="471e7-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="471e7-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="471e7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="471e7-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="471e7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="471e7-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="471e7-109">Attributes</span></span>  
  
|<span data-ttu-id="471e7-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="471e7-110">Attribute</span></span>|<span data-ttu-id="471e7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="471e7-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="471e7-112">name</span><span class="sxs-lookup"><span data-stu-id="471e7-112">name</span></span>|<span data-ttu-id="471e7-113">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="471e7-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="471e7-114">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="471e7-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="471e7-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="471e7-115">Child Elements</span></span>  
 <span data-ttu-id="471e7-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="471e7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="471e7-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="471e7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="471e7-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="471e7-118">Element</span></span>|<span data-ttu-id="471e7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="471e7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="471e7-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="471e7-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="471e7-121">Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="471e7-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="471e7-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="471e7-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
