---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 9b7092878c604142c29dcd8d27e3c458d203f9fa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399524"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="2a6e5-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="2a6e5-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="2a6e5-102">Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
<span data-ttu-id="2a6e5-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2a6e5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2a6e5-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2a6e5-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2a6e5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2a6e5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2a6e5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="2a6e5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="2a6e5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="2a6e5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2a6e5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> sslStreamSecurity**</span><span class="sxs-lookup"><span data-stu-id="2a6e5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a6e5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a6e5-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a6e5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2a6e5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2a6e5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a6e5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a6e5-112">Attributes</span></span>  
  
|<span data-ttu-id="2a6e5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="2a6e5-113">Attribute</span></span>|<span data-ttu-id="2a6e5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a6e5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a6e5-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="2a6e5-115">requireClientCertificate</span></span>|<span data-ttu-id="2a6e5-116">Um valor booliano que especifica se um certificado de cliente é necessário para essa associação.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="2a6e5-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-117">The default is `false`.</span></span>|  
|<span data-ttu-id="2a6e5-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="2a6e5-118">sslProtocols</span></span>|<span data-ttu-id="2a6e5-119">Um valor de sinalizador de enumeração SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="2a6e5-120">O padrão é Ssl3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a6e5-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2a6e5-121">Child Elements</span></span>  
 <span data-ttu-id="2a6e5-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a6e5-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a6e5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2a6e5-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a6e5-124">Element</span></span>|<span data-ttu-id="2a6e5-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a6e5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a6e5-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="2a6e5-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="2a6e5-127">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a6e5-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a6e5-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="2a6e5-129">Associações</span><span class="sxs-lookup"><span data-stu-id="2a6e5-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2a6e5-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="2a6e5-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2a6e5-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="2a6e5-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2a6e5-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2a6e5-132">\<customBinding></span></span>](custombinding.md)
