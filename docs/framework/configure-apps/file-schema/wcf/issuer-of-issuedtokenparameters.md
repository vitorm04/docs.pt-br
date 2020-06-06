---
title: <issuer> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397940"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="39c5c-102">\<issuer> de \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="39c5c-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="39c5c-103">Especifica o serviço de token de segurança (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="39c5c-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="39c5c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39c5c-104">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39c5c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="39c5c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="39c5c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="39c5c-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39c5c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="39c5c-107">Attributes</span></span>  
  
|<span data-ttu-id="39c5c-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="39c5c-108">Attribute</span></span>|<span data-ttu-id="39c5c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="39c5c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39c5c-110">address</span><span class="sxs-lookup"><span data-stu-id="39c5c-110">address</span></span>|<span data-ttu-id="39c5c-111">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="39c5c-111">Required string.</span></span> <span data-ttu-id="39c5c-112">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="39c5c-112">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39c5c-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="39c5c-113">Child Elements</span></span>  
  
|<span data-ttu-id="39c5c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="39c5c-114">Element</span></span>|<span data-ttu-id="39c5c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="39c5c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="39c5c-116">Uma coleção de cabeçalhos de endereço para os pontos de extremidade que o construtor pode criar.</span><span class="sxs-lookup"><span data-stu-id="39c5c-116">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="39c5c-117">Ao usar um token emitido, especifica as configurações que permitem que o cliente autentique o servidor.</span><span class="sxs-lookup"><span data-stu-id="39c5c-117">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39c5c-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="39c5c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="39c5c-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="39c5c-119">Element</span></span>|<span data-ttu-id="39c5c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="39c5c-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="39c5c-121">Especifica o token emitido atual.</span><span class="sxs-lookup"><span data-stu-id="39c5c-121">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39c5c-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="39c5c-122">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="39c5c-123">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="39c5c-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="39c5c-124">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="39c5c-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="39c5c-125">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="39c5c-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="39c5c-126">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="39c5c-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="39c5c-127">Associações</span><span class="sxs-lookup"><span data-stu-id="39c5c-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="39c5c-128">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="39c5c-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="39c5c-129">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="39c5c-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="39c5c-130">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="39c5c-130">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="39c5c-131">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="39c5c-131">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
