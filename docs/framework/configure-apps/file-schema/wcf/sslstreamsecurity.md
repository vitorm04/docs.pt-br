---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738597"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="09267-101">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="09267-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="09267-102">Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="09267-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
<span data-ttu-id="09267-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="09267-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="09267-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="09267-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="09267-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="09267-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="09267-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="09267-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="09267-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="09267-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="09267-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sslStreamSecurity >**</span><span class="sxs-lookup"><span data-stu-id="09267-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09267-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09267-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09267-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="09267-110">Attributes and Elements</span></span>  
 <span data-ttu-id="09267-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="09267-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09267-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="09267-112">Attributes</span></span>  
  
|<span data-ttu-id="09267-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="09267-113">Attribute</span></span>|<span data-ttu-id="09267-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="09267-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09267-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="09267-115">requireClientCertificate</span></span>|<span data-ttu-id="09267-116">Um valor booliano que especifica se um certificado de cliente é necessário para essa associação.</span><span class="sxs-lookup"><span data-stu-id="09267-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="09267-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="09267-117">The default is `false`.</span></span>|  
|<span data-ttu-id="09267-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="09267-118">sslProtocols</span></span>|<span data-ttu-id="09267-119">Um valor de sinalizador de enumeração SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="09267-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="09267-120">O padrão é Ssl3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="09267-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09267-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="09267-121">Child Elements</span></span>  
 <span data-ttu-id="09267-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="09267-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09267-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="09267-123">Parent Elements</span></span>  
  
|<span data-ttu-id="09267-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="09267-124">Element</span></span>|<span data-ttu-id="09267-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="09267-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09267-126">\<binding ></span><span class="sxs-lookup"><span data-stu-id="09267-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="09267-127">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="09267-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09267-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09267-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="09267-129">Associações</span><span class="sxs-lookup"><span data-stu-id="09267-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="09267-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="09267-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="09267-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="09267-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="09267-132">\<CustomBinding</span><span class="sxs-lookup"><span data-stu-id="09267-132">\<customBinding></span></span>](custombinding.md)
