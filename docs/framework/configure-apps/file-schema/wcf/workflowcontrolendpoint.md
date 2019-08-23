---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 2c9774217b835acdb9ebf7374b964d838497fc9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915329"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="dc3e0-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="dc3e0-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="dc3e0-102">Este elemento de configuração define um ponto de extremidade padrão para controlar a execução de instâncias de fluxo de trabalho (criar, executar, suspender, encerrar, etc.).</span><span class="sxs-lookup"><span data-stu-id="dc3e0-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="dc3e0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dc3e0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="dc3e0-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="dc3e0-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc3e0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc3e0-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc3e0-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dc3e0-106">Attributes and Elements</span></span>  
 <span data-ttu-id="dc3e0-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dc3e0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc3e0-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="dc3e0-108">Attributes</span></span>  
  
|<span data-ttu-id="dc3e0-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="dc3e0-109">Attribute</span></span>|<span data-ttu-id="dc3e0-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc3e0-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc3e0-111">name</span><span class="sxs-lookup"><span data-stu-id="dc3e0-111">name</span></span>|<span data-ttu-id="dc3e0-112">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="dc3e0-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="dc3e0-113">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="dc3e0-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc3e0-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dc3e0-114">Child Elements</span></span>  
 <span data-ttu-id="dc3e0-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="dc3e0-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc3e0-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dc3e0-116">Parent Elements</span></span>  
  
|<span data-ttu-id="dc3e0-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="dc3e0-117">Element</span></span>|<span data-ttu-id="dc3e0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc3e0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc3e0-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="dc3e0-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="dc3e0-120">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="dc3e0-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc3e0-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc3e0-121">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
