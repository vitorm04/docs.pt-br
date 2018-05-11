---
title: '&lt;cabeçalhos&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 7683b07093719cda6b210a4174d47e5785d4644d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltheadersgt"></a><span data-ttu-id="eee00-102">&lt;cabeçalhos&gt;</span><span class="sxs-lookup"><span data-stu-id="eee00-102">&lt;headers&gt;</span></span>
<span data-ttu-id="eee00-103">Um ponto de extremidade pode ser tratado por um ou mais cabeçalhos SOAP, além de seu URI básico.</span><span class="sxs-lookup"><span data-stu-id="eee00-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="eee00-104">Um conjunto de cenários em que isso é útil é um conjunto de cenários de intermediários SOAP em que um ponto de extremidade exige que os clientes do ponto de extremidade incluir cabeçalhos de SOAP direcionados a intermediários.</span><span class="sxs-lookup"><span data-stu-id="eee00-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="eee00-105">Este elemento de configuração pode ser usado para definir esses cabeçalhos de endereço personalizado.</span><span class="sxs-lookup"><span data-stu-id="eee00-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="eee00-106">As entradas na coleção de cabeçalho do ponto de extremidade são elementos XML definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="eee00-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="eee00-107">Cada elemento deve ser bem formado XML.</span><span class="sxs-lookup"><span data-stu-id="eee00-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="eee00-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eee00-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="eee00-109">\<client></span><span class="sxs-lookup"><span data-stu-id="eee00-109">\<client></span></span>  
<span data-ttu-id="eee00-110">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="eee00-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee00-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eee00-111">Syntax</span></span>  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eee00-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eee00-112">Attributes and Elements</span></span>  
 <span data-ttu-id="eee00-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eee00-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eee00-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="eee00-114">Attributes</span></span>  
 <span data-ttu-id="eee00-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="eee00-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eee00-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eee00-116">Child Elements</span></span>  
  
|<span data-ttu-id="eee00-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="eee00-117">Element</span></span>|<span data-ttu-id="eee00-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="eee00-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eee00-119">Região</span><span class="sxs-lookup"><span data-stu-id="eee00-119">Region</span></span>||  
|<span data-ttu-id="eee00-120">Membro</span><span class="sxs-lookup"><span data-stu-id="eee00-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="eee00-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eee00-121">Parent Elements</span></span>  
  
|<span data-ttu-id="eee00-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="eee00-122">Element</span></span>|<span data-ttu-id="eee00-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="eee00-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eee00-124">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="eee00-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="eee00-125">Configura os diferentes tipos de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="eee00-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eee00-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="eee00-126">Remarks</span></span>  
 <span data-ttu-id="eee00-127">Os cabeçalhos opcionais fornecem informações mais detalhadas de endereçamento para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="eee00-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="eee00-128">Por exemplo, os cabeçalhos podem indicar como processar uma mensagem de entrada, onde o ponto de extremidade deve enviar uma mensagem de resposta ou qual instância de um serviço para usar para processar uma mensagem de entrada de um determinado usuário quando houver várias instâncias.</span><span class="sxs-lookup"><span data-stu-id="eee00-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee00-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eee00-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="eee00-130">Pontos de extremidade: endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="eee00-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
