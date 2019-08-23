---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 8fcb5ac0c552d1ac2e849c95a5c0757d0c142f3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926391"
---
# <a name="behaviors"></a><span data-ttu-id="3ca6a-101">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="3ca6a-101">\<behaviors></span></span>
<span data-ttu-id="3ca6a-102">Esse elemento define duas coleções filho chamadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="3ca6a-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="3ca6a-103">Cada coleção define elementos de comportamento consumidos por pontos de extremidade e serviços, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3ca6a-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="3ca6a-104">Cada elemento do comportamento é identificado por seu exclusivo `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="3ca6a-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="3ca6a-105">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ca6a-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3ca6a-106">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3ca6a-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="3ca6a-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3ca6a-107">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ca6a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ca6a-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ca6a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3ca6a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3ca6a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3ca6a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ca6a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="3ca6a-111">Attributes</span></span>  
 <span data-ttu-id="3ca6a-112">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3ca6a-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3ca6a-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3ca6a-113">Child Elements</span></span>  
  
|<span data-ttu-id="3ca6a-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ca6a-114">Element</span></span>|<span data-ttu-id="3ca6a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ca6a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ca6a-116">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="3ca6a-116">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="3ca6a-117">Esta seção de configuração representa todos os comportamentos definidos para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="3ca6a-117">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="3ca6a-118">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3ca6a-118">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="3ca6a-119">Esta seção de configuração representa todos os comportamentos definidos para um serviço específico.</span><span class="sxs-lookup"><span data-stu-id="3ca6a-119">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ca6a-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3ca6a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3ca6a-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ca6a-121">Element</span></span>|<span data-ttu-id="3ca6a-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ca6a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ca6a-123">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3ca6a-123">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="3ca6a-124">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3ca6a-124">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ca6a-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ca6a-125">Remarks</span></span>  
 <span data-ttu-id="3ca6a-126">Você pode usar o `<remove>` elemento para remover um comportamento específico da coleção.</span><span class="sxs-lookup"><span data-stu-id="3ca6a-126">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="3ca6a-127">Para fazer isso, basta fornecer o nome do comportamento a ser removido no `name` atributo `<remove>` do elemento.</span><span class="sxs-lookup"><span data-stu-id="3ca6a-127">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="3ca6a-128">Você também pode usar o `<clear>` elemento para garantir que uma coleção de comportamentos comece vazia limpando todo o conteúdo da coleção.</span><span class="sxs-lookup"><span data-stu-id="3ca6a-128">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ca6a-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ca6a-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="3ca6a-130">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="3ca6a-130">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="3ca6a-131">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="3ca6a-131">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="3ca6a-132">Especificando o comportamento em tempo de execução do cliente</span><span class="sxs-lookup"><span data-stu-id="3ca6a-132">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="3ca6a-133">Especificando o comportamento em tempo de execução do serviço</span><span class="sxs-lookup"><span data-stu-id="3ca6a-133">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="3ca6a-134">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="3ca6a-134">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
