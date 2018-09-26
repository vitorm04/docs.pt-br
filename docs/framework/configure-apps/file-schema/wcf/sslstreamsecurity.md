---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
author: BrucePerlerMS
ms.openlocfilehash: 6eacf1833ecf980696d75c5dbcaaba3ba6403d92
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196324"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="0651a-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="0651a-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="0651a-103">Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="0651a-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="0651a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0651a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0651a-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="0651a-105">\<bindings></span></span>  
<span data-ttu-id="0651a-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0651a-106">\<customBinding></span></span>  
<span data-ttu-id="0651a-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="0651a-107">\<binding></span></span>  
<span data-ttu-id="0651a-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="0651a-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0651a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0651a-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0651a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0651a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0651a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0651a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0651a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="0651a-112">Attributes</span></span>  
  
|<span data-ttu-id="0651a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="0651a-113">Attribute</span></span>|<span data-ttu-id="0651a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0651a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0651a-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="0651a-115">requireClientCertificate</span></span>|<span data-ttu-id="0651a-116">Um valor booliano que especifica se um certificado de cliente é necessário para esta associação.</span><span class="sxs-lookup"><span data-stu-id="0651a-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="0651a-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="0651a-117">The default is `false`.</span></span>|  
|<span data-ttu-id="0651a-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="0651a-118">sslProtocols</span></span>|<span data-ttu-id="0651a-119">Um valor de sinalizador de enum de SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="0651a-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="0651a-120">O padrão é Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="0651a-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0651a-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0651a-121">Child Elements</span></span>  
 <span data-ttu-id="0651a-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0651a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0651a-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0651a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0651a-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="0651a-124">Element</span></span>|<span data-ttu-id="0651a-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="0651a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0651a-126">\<associação ></span><span class="sxs-lookup"><span data-stu-id="0651a-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0651a-127">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="0651a-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0651a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0651a-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="0651a-129">Associações</span><span class="sxs-lookup"><span data-stu-id="0651a-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0651a-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="0651a-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="0651a-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="0651a-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="0651a-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0651a-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
