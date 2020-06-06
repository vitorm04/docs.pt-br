---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738597"
---
# \<sslStreamSecurity>
<span data-ttu-id="5f45b-101">Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="5f45b-101">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="5f45b-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f45b-102">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f45b-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5f45b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5f45b-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5f45b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f45b-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="5f45b-105">Attributes</span></span>  
  
|<span data-ttu-id="5f45b-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="5f45b-106">Attribute</span></span>|<span data-ttu-id="5f45b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f45b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f45b-108">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="5f45b-108">requireClientCertificate</span></span>|<span data-ttu-id="5f45b-109">Um valor booliano que especifica se um certificado de cliente é necessário para essa associação.</span><span class="sxs-lookup"><span data-stu-id="5f45b-109">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="5f45b-110">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="5f45b-110">The default is `false`.</span></span>|  
|<span data-ttu-id="5f45b-111">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="5f45b-111">sslProtocols</span></span>|<span data-ttu-id="5f45b-112">Um valor de sinalizador de enumeração SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="5f45b-112">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="5f45b-113">O padrão é Ssl3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="5f45b-113">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f45b-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5f45b-114">Child Elements</span></span>  
 <span data-ttu-id="5f45b-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5f45b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f45b-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5f45b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5f45b-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="5f45b-117">Element</span></span>|<span data-ttu-id="5f45b-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f45b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="5f45b-119">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5f45b-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f45b-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="5f45b-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="5f45b-121">Associações</span><span class="sxs-lookup"><span data-stu-id="5f45b-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5f45b-122">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="5f45b-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5f45b-123">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5f45b-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
