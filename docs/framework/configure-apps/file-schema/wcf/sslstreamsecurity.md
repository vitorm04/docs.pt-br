---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
author: BrucePerlerMS
ms.openlocfilehash: 6eacf1833ecf980696d75c5dbcaaba3ba6403d92
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087444"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="5e290-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="5e290-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="5e290-103">Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="5e290-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="5e290-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5e290-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5e290-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="5e290-105">\<bindings></span></span>  
<span data-ttu-id="5e290-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5e290-106">\<customBinding></span></span>  
<span data-ttu-id="5e290-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="5e290-107">\<binding></span></span>  
<span data-ttu-id="5e290-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="5e290-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e290-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e290-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e290-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5e290-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5e290-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5e290-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e290-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e290-112">Attributes</span></span>  
  
|<span data-ttu-id="5e290-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5e290-113">Attribute</span></span>|<span data-ttu-id="5e290-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e290-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e290-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="5e290-115">requireClientCertificate</span></span>|<span data-ttu-id="5e290-116">Um valor booliano que especifica se um certificado de cliente é necessário para esta associação.</span><span class="sxs-lookup"><span data-stu-id="5e290-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="5e290-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="5e290-117">The default is `false`.</span></span>|  
|<span data-ttu-id="5e290-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="5e290-118">sslProtocols</span></span>|<span data-ttu-id="5e290-119">Um valor de sinalizador de enum de SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="5e290-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="5e290-120">O padrão é Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="5e290-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e290-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5e290-121">Child Elements</span></span>  
 <span data-ttu-id="5e290-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5e290-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e290-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e290-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5e290-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e290-124">Element</span></span>|<span data-ttu-id="5e290-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e290-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e290-126">\<associação ></span><span class="sxs-lookup"><span data-stu-id="5e290-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="5e290-127">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5e290-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e290-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e290-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="5e290-129">Associações</span><span class="sxs-lookup"><span data-stu-id="5e290-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5e290-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="5e290-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="5e290-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5e290-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="5e290-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5e290-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
