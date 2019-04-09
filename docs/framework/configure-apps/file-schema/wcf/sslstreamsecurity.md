---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 67ec30b2bf3c322b949700789ce942e4281b77a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204439"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="75d98-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="75d98-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="75d98-102">Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="75d98-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="75d98-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="75d98-103">\<system.serviceModel></span></span>  
<span data-ttu-id="75d98-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="75d98-104">\<bindings></span></span>  
<span data-ttu-id="75d98-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="75d98-105">\<customBinding></span></span>  
<span data-ttu-id="75d98-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="75d98-106">\<binding></span></span>  
<span data-ttu-id="75d98-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="75d98-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75d98-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75d98-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75d98-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="75d98-109">Attributes and Elements</span></span>  
 <span data-ttu-id="75d98-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="75d98-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75d98-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="75d98-111">Attributes</span></span>  
  
|<span data-ttu-id="75d98-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="75d98-112">Attribute</span></span>|<span data-ttu-id="75d98-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="75d98-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75d98-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="75d98-114">requireClientCertificate</span></span>|<span data-ttu-id="75d98-115">Um valor booliano que especifica se um certificado de cliente é necessário para esta associação.</span><span class="sxs-lookup"><span data-stu-id="75d98-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="75d98-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="75d98-116">The default is `false`.</span></span>|  
|<span data-ttu-id="75d98-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="75d98-117">sslProtocols</span></span>|<span data-ttu-id="75d98-118">Um valor de sinalizador de enum de SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="75d98-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="75d98-119">O padrão é Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="75d98-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75d98-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="75d98-120">Child Elements</span></span>  
 <span data-ttu-id="75d98-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="75d98-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75d98-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="75d98-122">Parent Elements</span></span>  
  
|<span data-ttu-id="75d98-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="75d98-123">Element</span></span>|<span data-ttu-id="75d98-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="75d98-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75d98-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="75d98-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="75d98-126">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="75d98-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75d98-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75d98-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="75d98-128">Associações</span><span class="sxs-lookup"><span data-stu-id="75d98-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="75d98-129">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="75d98-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="75d98-130">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="75d98-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="75d98-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="75d98-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
