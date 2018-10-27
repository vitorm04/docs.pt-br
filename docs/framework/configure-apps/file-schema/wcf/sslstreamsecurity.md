---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: ecc67c2b3972ccb5bc8a1fe9ae9b400292642d53
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184485"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="9a8da-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="9a8da-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="9a8da-103">Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="9a8da-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="9a8da-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9a8da-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9a8da-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="9a8da-105">\<bindings></span></span>  
<span data-ttu-id="9a8da-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9a8da-106">\<customBinding></span></span>  
<span data-ttu-id="9a8da-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="9a8da-107">\<binding></span></span>  
<span data-ttu-id="9a8da-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="9a8da-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a8da-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a8da-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a8da-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9a8da-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9a8da-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9a8da-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a8da-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a8da-112">Attributes</span></span>  
  
|<span data-ttu-id="9a8da-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="9a8da-113">Attribute</span></span>|<span data-ttu-id="9a8da-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a8da-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9a8da-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="9a8da-115">requireClientCertificate</span></span>|<span data-ttu-id="9a8da-116">Um valor booliano que especifica se um certificado de cliente é necessário para esta associação.</span><span class="sxs-lookup"><span data-stu-id="9a8da-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="9a8da-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="9a8da-117">The default is `false`.</span></span>|  
|<span data-ttu-id="9a8da-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="9a8da-118">sslProtocols</span></span>|<span data-ttu-id="9a8da-119">Um valor de sinalizador de enum de SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="9a8da-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="9a8da-120">O padrão é Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="9a8da-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a8da-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9a8da-121">Child Elements</span></span>  
 <span data-ttu-id="9a8da-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9a8da-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a8da-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9a8da-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9a8da-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a8da-124">Element</span></span>|<span data-ttu-id="9a8da-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a8da-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a8da-126">\<associação ></span><span class="sxs-lookup"><span data-stu-id="9a8da-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="9a8da-127">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="9a8da-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a8da-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a8da-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="9a8da-129">Associações</span><span class="sxs-lookup"><span data-stu-id="9a8da-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9a8da-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="9a8da-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9a8da-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="9a8da-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9a8da-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9a8da-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
