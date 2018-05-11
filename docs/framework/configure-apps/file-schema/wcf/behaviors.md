---
title: '&lt;Comportamentos&gt;'
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: ca9cf5daa6590c14d4b5fd15c502d67af1f93b52
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbehaviorsgt"></a><span data-ttu-id="3228f-102">&lt;Comportamentos&gt;</span><span class="sxs-lookup"><span data-stu-id="3228f-102">&lt;behaviors&gt;</span></span>
<span data-ttu-id="3228f-103">Este elemento define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="3228f-103">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="3228f-104">Cada coleção define elementos de comportamento consumidos pelos pontos de extremidade e serviços, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3228f-104">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="3228f-105">Cada elemento do comportamento é identificado por seu exclusivo `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="3228f-105">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="3228f-106">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="3228f-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3228f-107">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3228f-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="3228f-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3228f-108">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3228f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3228f-109">Syntax</span></span>  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
   </serviceBehaviors>  
   <endpointBehaviors>  
   </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3228f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3228f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3228f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3228f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3228f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3228f-112">Attributes</span></span>  
 <span data-ttu-id="3228f-113">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3228f-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3228f-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3228f-114">Child Elements</span></span>  
  
|<span data-ttu-id="3228f-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="3228f-115">Element</span></span>|<span data-ttu-id="3228f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="3228f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3228f-117">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3228f-117">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="3228f-118">Esta seção de configuração representa todos os comportamentos definidos para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="3228f-118">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="3228f-119">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3228f-119">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="3228f-120">Esta seção de configuração representa todos os comportamentos definidos para um serviço específico.</span><span class="sxs-lookup"><span data-stu-id="3228f-120">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3228f-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3228f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3228f-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="3228f-122">Element</span></span>|<span data-ttu-id="3228f-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="3228f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3228f-124">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3228f-124">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="3228f-125">O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3228f-125">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3228f-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="3228f-126">Remarks</span></span>  
 <span data-ttu-id="3228f-127">Você pode usar o `<remove>` elemento para remover um comportamento específico da coleção.</span><span class="sxs-lookup"><span data-stu-id="3228f-127">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="3228f-128">Para fazer isso, basta fornecer o nome do comportamento para remover o `name` atributo o `<remove>` elemento.</span><span class="sxs-lookup"><span data-stu-id="3228f-128">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="3228f-129">Você também pode usar o `<clear>` elemento para garantir que uma coleção de comportamento começa vazia limpando todo o conteúdo da coleção.</span><span class="sxs-lookup"><span data-stu-id="3228f-129">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3228f-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3228f-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="3228f-131">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="3228f-131">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 [<span data-ttu-id="3228f-132">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="3228f-132">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="3228f-133">Especificando o comportamento em tempo de execução do cliente</span><span class="sxs-lookup"><span data-stu-id="3228f-133">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [<span data-ttu-id="3228f-134">Especificando o comportamento em tempo de execução do serviço</span><span class="sxs-lookup"><span data-stu-id="3228f-134">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)  
 [<span data-ttu-id="3228f-135">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="3228f-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
