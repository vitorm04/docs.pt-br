---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: a9c16d1036a8177120cd152d4ac211ad084d588e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150378"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="32f86-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="32f86-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="32f86-102">Este elemento de configuração define um ponto de extremidade padrão para controlar a execução de instâncias de fluxo de trabalho (criar, executar, suspender, finalizar, etc).</span><span class="sxs-lookup"><span data-stu-id="32f86-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="32f86-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="32f86-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="32f86-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="32f86-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32f86-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32f86-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32f86-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="32f86-106">Attributes and Elements</span></span>  
 <span data-ttu-id="32f86-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="32f86-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32f86-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="32f86-108">Attributes</span></span>  
  
|<span data-ttu-id="32f86-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="32f86-109">Attribute</span></span>|<span data-ttu-id="32f86-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="32f86-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32f86-111">name</span><span class="sxs-lookup"><span data-stu-id="32f86-111">name</span></span>|<span data-ttu-id="32f86-112">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="32f86-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="32f86-113">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="32f86-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32f86-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="32f86-114">Child Elements</span></span>  
 <span data-ttu-id="32f86-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="32f86-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32f86-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="32f86-116">Parent Elements</span></span>  
  
|<span data-ttu-id="32f86-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="32f86-117">Element</span></span>|<span data-ttu-id="32f86-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="32f86-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32f86-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="32f86-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="32f86-120">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="32f86-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32f86-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32f86-121">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
