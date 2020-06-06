---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855175"
---
# \<headers>
<span data-ttu-id="de203-101">Um ponto de extremidade pode ser resolvido por um ou mais cabeçalhos SOAP além de seu URI básico.</span><span class="sxs-lookup"><span data-stu-id="de203-101">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="de203-102">Um conjunto de cenários em que isso é útil é um conjunto de cenários intermediários de SOAP em que um ponto de extremidade exige que clientes desse ponto de extremidade incluam cabeçalhos SOAP direcionados a intermediários.</span><span class="sxs-lookup"><span data-stu-id="de203-102">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="de203-103">Este elemento de configuração pode ser usado para definir esses cabeçalhos de endereço personalizados.</span><span class="sxs-lookup"><span data-stu-id="de203-103">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="de203-104">As entradas na coleção de cabeçalhos do ponto de extremidade são elementos XML definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="de203-104">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="de203-105">Cada elemento deve ser um XML bem formado.</span><span class="sxs-lookup"><span data-stu-id="de203-105">Each element has to be well-formed XML.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**  
  
## <a name="syntax"></a><span data-ttu-id="de203-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de203-106">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de203-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="de203-107">Attributes and Elements</span></span>  
 <span data-ttu-id="de203-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="de203-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de203-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="de203-109">Attributes</span></span>  
 <span data-ttu-id="de203-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="de203-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de203-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="de203-111">Child Elements</span></span>  
 <span data-ttu-id="de203-112">Elementos XML definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="de203-112">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de203-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="de203-113">Parent Elements</span></span>  
  
|<span data-ttu-id="de203-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="de203-114">Element</span></span>|<span data-ttu-id="de203-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="de203-115">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="de203-116">Configura tipos diferentes de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="de203-116">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de203-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="de203-117">Remarks</span></span>  
 <span data-ttu-id="de203-118">Os cabeçalhos opcionais fornecem informações de endereçamento mais detalhadas para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="de203-118">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="de203-119">Por exemplo, os cabeçalhos podem indicar como processar uma mensagem de entrada, em que o ponto de extremidade deve enviar uma mensagem de resposta ou qual instância de um serviço usar para processar uma mensagem de entrada de um usuário específico quando várias instâncias estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="de203-119">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de203-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="de203-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="de203-121">Pontos de extremidade: endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="de203-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
