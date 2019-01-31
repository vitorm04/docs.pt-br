---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: de0a51ed6f2a878ab3a6ebe15863f1f2925034ce
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272569"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="5a734-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="5a734-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="5a734-102">Este elemento de configuração define um ponto de extremidade padrão para controlar a execução de instâncias de fluxo de trabalho (criar, executar, suspender, finalizar, etc).</span><span class="sxs-lookup"><span data-stu-id="5a734-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="5a734-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5a734-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a734-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="5a734-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a734-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a734-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a734-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5a734-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5a734-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5a734-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a734-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="5a734-108">Attributes</span></span>  
  
|<span data-ttu-id="5a734-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="5a734-109">Attribute</span></span>|<span data-ttu-id="5a734-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a734-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a734-111">name</span><span class="sxs-lookup"><span data-stu-id="5a734-111">name</span></span>|<span data-ttu-id="5a734-112">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="5a734-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="5a734-113">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="5a734-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a734-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5a734-114">Child Elements</span></span>  
 <span data-ttu-id="5a734-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5a734-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a734-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5a734-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5a734-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="5a734-117">Element</span></span>|<span data-ttu-id="5a734-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a734-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a734-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="5a734-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="5a734-120">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="5a734-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a734-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a734-121">See also</span></span>
- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
