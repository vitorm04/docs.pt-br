---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 5ed87adfb3963513602844fc69afce8f7994fa8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932431"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="bfe22-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="bfe22-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="bfe22-102">Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="bfe22-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="bfe22-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bfe22-103">\<system.serviceModel></span></span>  
<span data-ttu-id="bfe22-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="bfe22-104">\<bindings></span></span>  
<span data-ttu-id="bfe22-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bfe22-105">\<customBinding></span></span>  
<span data-ttu-id="bfe22-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="bfe22-106">\<binding></span></span>  
<span data-ttu-id="bfe22-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="bfe22-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfe22-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfe22-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfe22-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bfe22-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bfe22-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bfe22-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfe22-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="bfe22-111">Attributes</span></span>  
  
|<span data-ttu-id="bfe22-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="bfe22-112">Attribute</span></span>|<span data-ttu-id="bfe22-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfe22-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bfe22-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="bfe22-114">requireClientCertificate</span></span>|<span data-ttu-id="bfe22-115">Um valor booliano que especifica se um certificado de cliente é necessário para essa associação.</span><span class="sxs-lookup"><span data-stu-id="bfe22-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="bfe22-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="bfe22-116">The default is `false`.</span></span>|  
|<span data-ttu-id="bfe22-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="bfe22-117">sslProtocols</span></span>|<span data-ttu-id="bfe22-118">Um valor de sinalizador de enumeração SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="bfe22-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="bfe22-119">O padrão é Ssl3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="bfe22-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfe22-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bfe22-120">Child Elements</span></span>  
 <span data-ttu-id="bfe22-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bfe22-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfe22-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bfe22-122">Parent Elements</span></span>  
  
|<span data-ttu-id="bfe22-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="bfe22-123">Element</span></span>|<span data-ttu-id="bfe22-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfe22-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bfe22-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="bfe22-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="bfe22-126">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="bfe22-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bfe22-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfe22-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="bfe22-128">Associações</span><span class="sxs-lookup"><span data-stu-id="bfe22-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bfe22-129">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="bfe22-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bfe22-130">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="bfe22-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bfe22-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bfe22-131">\<customBinding></span></span>](custombinding.md)
