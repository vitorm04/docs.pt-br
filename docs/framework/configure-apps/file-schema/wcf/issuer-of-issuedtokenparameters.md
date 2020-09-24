---
title: <issuer> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bfe8163d2d6baba1d6e8053f7f6579673d8b4b21
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157272"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="1dc63-102">\<issuer> de \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="1dc63-102">\<issuer> of \<issuedTokenParameters></span></span>

<span data-ttu-id="1dc63-103">Especifica o serviço de token de segurança (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="1dc63-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="1dc63-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1dc63-104">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dc63-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1dc63-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1dc63-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="1dc63-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dc63-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="1dc63-107">Attributes</span></span>  
  
|<span data-ttu-id="1dc63-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="1dc63-108">Attribute</span></span>|<span data-ttu-id="1dc63-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dc63-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1dc63-110">address</span><span class="sxs-lookup"><span data-stu-id="1dc63-110">address</span></span>|<span data-ttu-id="1dc63-111">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="1dc63-111">Required string.</span></span> <span data-ttu-id="1dc63-112">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="1dc63-112">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1dc63-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1dc63-113">Child Elements</span></span>  
  
|<span data-ttu-id="1dc63-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1dc63-114">Element</span></span>|<span data-ttu-id="1dc63-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dc63-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="1dc63-116">Uma coleção de cabeçalhos de endereço para os pontos de extremidade que o construtor pode criar.</span><span class="sxs-lookup"><span data-stu-id="1dc63-116">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="1dc63-117">Ao usar um token emitido, especifica as configurações que permitem que o cliente autentique o servidor.</span><span class="sxs-lookup"><span data-stu-id="1dc63-117">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1dc63-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1dc63-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1dc63-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="1dc63-119">Element</span></span>|<span data-ttu-id="1dc63-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dc63-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="1dc63-121">Especifica o token emitido atual.</span><span class="sxs-lookup"><span data-stu-id="1dc63-121">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1dc63-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="1dc63-122">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1dc63-123">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="1dc63-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1dc63-124">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="1dc63-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1dc63-125">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="1dc63-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="1dc63-126">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="1dc63-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1dc63-127">Associações</span><span class="sxs-lookup"><span data-stu-id="1dc63-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1dc63-128">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="1dc63-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1dc63-129">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="1dc63-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="1dc63-130">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="1dc63-130">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="1dc63-131">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="1dc63-131">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
