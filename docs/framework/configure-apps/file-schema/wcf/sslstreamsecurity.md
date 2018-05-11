---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a86e1aae7ddd5389f098e532ae2c2cc67f4085e3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="c1fd7-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="c1fd7-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="c1fd7-103">Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="c1fd7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c1fd7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c1fd7-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="c1fd7-105">\<bindings></span></span>  
<span data-ttu-id="c1fd7-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c1fd7-106">\<customBinding></span></span>  
<span data-ttu-id="c1fd7-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c1fd7-107">\<binding></span></span>  
<span data-ttu-id="c1fd7-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="c1fd7-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1fd7-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1fd7-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1fd7-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c1fd7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c1fd7-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1fd7-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c1fd7-112">Attributes</span></span>  
  
|<span data-ttu-id="c1fd7-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="c1fd7-113">Attribute</span></span>|<span data-ttu-id="c1fd7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1fd7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1fd7-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="c1fd7-115">requireClientCertificate</span></span>|<span data-ttu-id="c1fd7-116">Um valor booleano que especifica se um certificado de cliente é necessário para essa associação.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="c1fd7-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-117">The default is `false`.</span></span>|  
|<span data-ttu-id="c1fd7-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="c1fd7-118">sslProtocols</span></span>|<span data-ttu-id="c1fd7-119">Um valor de sinalizador de enumeração de SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="c1fd7-120">O padrão é Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1fd7-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c1fd7-121">Child Elements</span></span>  
 <span data-ttu-id="c1fd7-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1fd7-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c1fd7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c1fd7-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="c1fd7-124">Element</span></span>|<span data-ttu-id="c1fd7-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1fd7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1fd7-126">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c1fd7-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c1fd7-127">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1fd7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1fd7-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="c1fd7-129">Associações</span><span class="sxs-lookup"><span data-stu-id="c1fd7-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c1fd7-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="c1fd7-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c1fd7-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c1fd7-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c1fd7-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c1fd7-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
