---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 67ec30b2bf3c322b949700789ce942e4281b77a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757983"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="3de2f-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="3de2f-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="3de2f-102">Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="3de2f-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="3de2f-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3de2f-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3de2f-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3de2f-104">\<bindings></span></span>  
<span data-ttu-id="3de2f-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3de2f-105">\<customBinding></span></span>  
<span data-ttu-id="3de2f-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="3de2f-106">\<binding></span></span>  
<span data-ttu-id="3de2f-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="3de2f-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de2f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3de2f-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3de2f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3de2f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3de2f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3de2f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3de2f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="3de2f-111">Attributes</span></span>  
  
|<span data-ttu-id="3de2f-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="3de2f-112">Attribute</span></span>|<span data-ttu-id="3de2f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3de2f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3de2f-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="3de2f-114">requireClientCertificate</span></span>|<span data-ttu-id="3de2f-115">Um valor booliano que especifica se um certificado de cliente é necessário para esta associação.</span><span class="sxs-lookup"><span data-stu-id="3de2f-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="3de2f-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="3de2f-116">The default is `false`.</span></span>|  
|<span data-ttu-id="3de2f-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="3de2f-117">sslProtocols</span></span>|<span data-ttu-id="3de2f-118">Um valor de sinalizador de enum de SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="3de2f-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="3de2f-119">O padrão é Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="3de2f-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3de2f-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3de2f-120">Child Elements</span></span>  
 <span data-ttu-id="3de2f-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3de2f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3de2f-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3de2f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3de2f-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="3de2f-123">Element</span></span>|<span data-ttu-id="3de2f-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="3de2f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3de2f-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="3de2f-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3de2f-126">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="3de2f-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3de2f-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3de2f-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="3de2f-128">Associações</span><span class="sxs-lookup"><span data-stu-id="3de2f-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3de2f-129">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="3de2f-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3de2f-130">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="3de2f-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3de2f-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3de2f-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
