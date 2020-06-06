---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: bcdd26f038b343040d81b0add83bf166a5e3151f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139695"
---
# \<behaviors>
<span data-ttu-id="f7533-101">Esse elemento define duas coleções filho chamadas `endpointBehaviors` e `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="f7533-101">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="f7533-102">Cada coleção define elementos de comportamento consumidos por pontos de extremidade e serviços, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f7533-102">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="f7533-103">Cada elemento do comportamento é identificado por seu exclusivo `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="f7533-103">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="f7533-104">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="f7533-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f7533-105">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f7533-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="f7533-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7533-106">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7533-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f7533-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f7533-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f7533-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7533-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f7533-109">Attributes</span></span>  
 <span data-ttu-id="f7533-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f7533-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f7533-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f7533-111">Child Elements</span></span>  
  
|<span data-ttu-id="f7533-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7533-112">Element</span></span>|<span data-ttu-id="f7533-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7533-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="f7533-114">Esta seção de configuração representa todos os comportamentos definidos para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="f7533-114">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="f7533-115">Esta seção de configuração representa todos os comportamentos definidos para um serviço específico.</span><span class="sxs-lookup"><span data-stu-id="f7533-115">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7533-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f7533-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f7533-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7533-117">Element</span></span>|<span data-ttu-id="f7533-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7533-118">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="f7533-119">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f7533-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7533-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7533-120">Remarks</span></span>  
 <span data-ttu-id="f7533-121">Você pode usar o `<remove>` elemento para remover um comportamento específico da coleção.</span><span class="sxs-lookup"><span data-stu-id="f7533-121">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="f7533-122">Para fazer isso, basta fornecer o nome do comportamento a ser removido no `name` atributo do `<remove>` elemento.</span><span class="sxs-lookup"><span data-stu-id="f7533-122">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="f7533-123">Você também pode usar o `<clear>` elemento para garantir que uma coleção de comportamentos comece vazia limpando todo o conteúdo da coleção.</span><span class="sxs-lookup"><span data-stu-id="f7533-123">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7533-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="f7533-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="f7533-125">Configurando e estendendo o runtime com comportamentos</span><span class="sxs-lookup"><span data-stu-id="f7533-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="f7533-126">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="f7533-126">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="f7533-127">Especificando o comportamento em tempo de execução do cliente</span><span class="sxs-lookup"><span data-stu-id="f7533-127">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="f7533-128">Especificando o comportamento em tempo de execução do serviço</span><span class="sxs-lookup"><span data-stu-id="f7533-128">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="f7533-129">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="f7533-129">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
