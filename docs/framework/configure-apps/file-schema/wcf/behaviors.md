---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 108c349a44ed3ac902652f86241c1e96a622549b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204231"
---
# <a name="behaviors"></a><span data-ttu-id="51630-101">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="51630-101">\<behaviors></span></span>
<span data-ttu-id="51630-102">Este elemento define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="51630-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="51630-103">Cada coleção define elementos de comportamento consumidos pelos pontos de extremidade e serviços, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="51630-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="51630-104">Cada elemento do comportamento é identificado por seu exclusivo `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="51630-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="51630-105">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="51630-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="51630-106">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="51630-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="51630-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="51630-107">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51630-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51630-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51630-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="51630-109">Attributes and Elements</span></span>  
 <span data-ttu-id="51630-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="51630-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51630-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="51630-111">Attributes</span></span>  
 <span data-ttu-id="51630-112">Nenhum</span><span class="sxs-lookup"><span data-stu-id="51630-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="51630-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="51630-113">Child Elements</span></span>  
  
|<span data-ttu-id="51630-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="51630-114">Element</span></span>|<span data-ttu-id="51630-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="51630-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51630-116">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="51630-116">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="51630-117">Esta seção de configuração representa todos os comportamentos definidos para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="51630-117">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="51630-118">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="51630-118">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="51630-119">Esta seção de configuração representa todos os comportamentos definidos para um serviço específico.</span><span class="sxs-lookup"><span data-stu-id="51630-119">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="51630-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="51630-120">Parent Elements</span></span>  
  
|<span data-ttu-id="51630-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="51630-121">Element</span></span>|<span data-ttu-id="51630-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="51630-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51630-123">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="51630-123">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="51630-124">O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="51630-124">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51630-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="51630-125">Remarks</span></span>  
 <span data-ttu-id="51630-126">Você pode usar o `<remove>` elemento do qual remover um comportamento específico da coleção.</span><span class="sxs-lookup"><span data-stu-id="51630-126">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="51630-127">Para fazer isso, basta fornecer o nome do comportamento para remover o `name` atributo do `<remove>` elemento.</span><span class="sxs-lookup"><span data-stu-id="51630-127">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="51630-128">Você também pode usar o `<clear>` elemento para garantir que uma coleção de comportamentos começa vazia limpando todo o conteúdo da coleção.</span><span class="sxs-lookup"><span data-stu-id="51630-128">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51630-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51630-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="51630-130">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="51630-130">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="51630-131">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="51630-131">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="51630-132">Especificando o comportamento em tempo de execução do cliente</span><span class="sxs-lookup"><span data-stu-id="51630-132">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="51630-133">Especificando o comportamento em tempo de execução do serviço</span><span class="sxs-lookup"><span data-stu-id="51630-133">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="51630-134">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="51630-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
