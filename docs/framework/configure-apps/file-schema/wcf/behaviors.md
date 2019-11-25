---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: bcdd26f038b343040d81b0add83bf166a5e3151f
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139695"
---
# <a name="behaviors"></a><span data-ttu-id="28686-101">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="28686-101">\<behaviors></span></span>
<span data-ttu-id="28686-102">Esse elemento define duas coleções filhas chamadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="28686-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="28686-103">Cada coleção define elementos de comportamento consumidos por pontos de extremidade e serviços, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="28686-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="28686-104">Cada elemento do comportamento é identificado por seu exclusivo `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="28686-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="28686-105">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="28686-105">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="28686-106">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="28686-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
<span data-ttu-id="28686-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="28686-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="28686-108">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="28686-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="28686-109">&nbsp;&nbsp;&nbsp;&nbsp; **\<comportamentos >**</span><span class="sxs-lookup"><span data-stu-id="28686-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28686-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28686-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28686-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="28686-111">Attributes and Elements</span></span>  
 <span data-ttu-id="28686-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="28686-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28686-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="28686-113">Attributes</span></span>  
 <span data-ttu-id="28686-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="28686-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="28686-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="28686-115">Child Elements</span></span>  
  
|<span data-ttu-id="28686-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="28686-116">Element</span></span>|<span data-ttu-id="28686-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="28686-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28686-118">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="28686-118">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="28686-119">Esta seção de configuração representa todos os comportamentos definidos para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="28686-119">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="28686-120">> de \<de portais</span><span class="sxs-lookup"><span data-stu-id="28686-120">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="28686-121">Esta seção de configuração representa todos os comportamentos definidos para um serviço específico.</span><span class="sxs-lookup"><span data-stu-id="28686-121">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28686-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="28686-122">Parent Elements</span></span>  
  
|<span data-ttu-id="28686-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="28686-123">Element</span></span>|<span data-ttu-id="28686-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="28686-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28686-125">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="28686-125">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="28686-126">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="28686-126">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28686-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="28686-127">Remarks</span></span>  
 <span data-ttu-id="28686-128">Você pode usar o elemento `<remove>` para remover um comportamento específico da coleção.</span><span class="sxs-lookup"><span data-stu-id="28686-128">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="28686-129">Para fazer isso, basta fornecer o nome do comportamento a ser removido no atributo `name` do elemento `<remove>`.</span><span class="sxs-lookup"><span data-stu-id="28686-129">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="28686-130">Você também pode usar o elemento `<clear>` para garantir que uma coleção de comportamentos comece vazia limpando todo o conteúdo da coleção.</span><span class="sxs-lookup"><span data-stu-id="28686-130">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28686-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28686-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="28686-132">Configurando e estendendo o runtime com comportamentos</span><span class="sxs-lookup"><span data-stu-id="28686-132">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="28686-133">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="28686-133">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="28686-134">Especificando o comportamento em tempo de execução do cliente</span><span class="sxs-lookup"><span data-stu-id="28686-134">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="28686-135">Especificando o comportamento em tempo de execução do serviço</span><span class="sxs-lookup"><span data-stu-id="28686-135">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="28686-136">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="28686-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
