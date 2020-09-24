---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: aa6bc7f5a94afc8a190d3d9d2d71ea8b38d8c25b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153567"
---
# \<sslStreamSecurity>

<span data-ttu-id="91065-101">Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="91065-101">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="91065-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="91065-102">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91065-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="91065-103">Attributes and Elements</span></span>  

 <span data-ttu-id="91065-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="91065-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91065-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="91065-105">Attributes</span></span>  
  
|<span data-ttu-id="91065-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="91065-106">Attribute</span></span>|<span data-ttu-id="91065-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="91065-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91065-108">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="91065-108">requireClientCertificate</span></span>|<span data-ttu-id="91065-109">Um valor booliano que especifica se um certificado de cliente é necessário para essa associação.</span><span class="sxs-lookup"><span data-stu-id="91065-109">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="91065-110">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="91065-110">The default is `false`.</span></span>|  
|<span data-ttu-id="91065-111">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="91065-111">sslProtocols</span></span>|<span data-ttu-id="91065-112">Um valor de sinalizador de enumeração SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="91065-112">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="91065-113">O padrão é Ssl3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="91065-113">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91065-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="91065-114">Child Elements</span></span>  

 <span data-ttu-id="91065-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="91065-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91065-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="91065-116">Parent Elements</span></span>  
  
|<span data-ttu-id="91065-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="91065-117">Element</span></span>|<span data-ttu-id="91065-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="91065-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="91065-119">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="91065-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91065-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="91065-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="91065-121">Associações</span><span class="sxs-lookup"><span data-stu-id="91065-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="91065-122">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="91065-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="91065-123">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="91065-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
