---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 4077aacab1c1c4594db76cc6663bfc0245d345d7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555491"
---
# \<custom>
<span data-ttu-id="1d56b-101">Especifica as configurações para um serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="1d56b-101">Specifies settings for a custom peer resolver service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a><span data-ttu-id="1d56b-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d56b-102">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d56b-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1d56b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1d56b-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1d56b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d56b-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="1d56b-105">Attributes</span></span>  
  
|<span data-ttu-id="1d56b-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="1d56b-106">Attribute</span></span>|<span data-ttu-id="1d56b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d56b-107">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="1d56b-108">Um URI que especifica o endereço do ponto de extremidade do nó par que hospeda o serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="1d56b-108">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="1d56b-109">Uma cadeia de caracteres que especifica o tipo do serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="1d56b-109">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d56b-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1d56b-110">Child Elements</span></span>  
  
|<span data-ttu-id="1d56b-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d56b-111">Element</span></span>|<span data-ttu-id="1d56b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d56b-112">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="1d56b-113">Especifica a identidade para resolvedores de pares personalizados configurados com este elemento.</span><span class="sxs-lookup"><span data-stu-id="1d56b-113">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="1d56b-114">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IdentityElement> .</span><span class="sxs-lookup"><span data-stu-id="1d56b-114">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="1d56b-115">Uma coleção de cabeçalho de endereço usada para mensagens SOAP tratadas pelo resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="1d56b-115">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d56b-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1d56b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1d56b-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d56b-117">Element</span></span>|<span data-ttu-id="1d56b-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d56b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|<span data-ttu-id="1d56b-119">Um resolvedor de pares que é usado para resolver uma ID de malha de mesmo nível para um conjunto de endereços de nó par que representa vários nós que participam da malha.</span><span class="sxs-lookup"><span data-stu-id="1d56b-119">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d56b-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d56b-120">Remarks</span></span>  
 <span data-ttu-id="1d56b-121">Esse elemento define as configurações básicas para um serviço resolvedor de pares personalizado, incluindo o endereço do ponto de extremidade do par que hospeda o serviço e quaisquer configurações de associação específicas.</span><span class="sxs-lookup"><span data-stu-id="1d56b-121">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="1d56b-122">Para obter mais informações sobre como criar um resolvedor personalizado, consulte [adicionando um resolvedor personalizado a um aplicativo PeerChannel](/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1d56b-122">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d56b-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="1d56b-123">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="1d56b-124">Resolvedor peer</span><span class="sxs-lookup"><span data-stu-id="1d56b-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="1d56b-125">[Adicionando um resolvedor personalizado a um aplicativo PeerChannel](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1d56b-125">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>
