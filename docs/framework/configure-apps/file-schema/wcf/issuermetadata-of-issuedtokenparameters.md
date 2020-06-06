---
title: <issuerMetadata> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400348"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="ada1d-102">\<issuerMetadata> de \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="ada1d-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="ada1d-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ada1d-103">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ada1d-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ada1d-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ada1d-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ada1d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ada1d-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="ada1d-106">Attributes</span></span>  
  
|<span data-ttu-id="ada1d-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="ada1d-107">Attribute</span></span>|<span data-ttu-id="ada1d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ada1d-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ada1d-109">address</span><span class="sxs-lookup"><span data-stu-id="ada1d-109">address</span></span>|<span data-ttu-id="ada1d-110">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="ada1d-110">Required.</span></span> <span data-ttu-id="ada1d-111">Uma cadeia de caracteres que especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ada1d-111">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="ada1d-112">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="ada1d-112">The address must be an absolute URI.</span></span> <span data-ttu-id="ada1d-113">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="ada1d-113">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ada1d-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ada1d-114">Child Elements</span></span>  
  
|<span data-ttu-id="ada1d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="ada1d-115">Element</span></span>|<span data-ttu-id="ada1d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ada1d-116">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="ada1d-117">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="ada1d-117">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="ada1d-118">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="ada1d-118">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ada1d-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ada1d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ada1d-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="ada1d-120">Element</span></span>|<span data-ttu-id="ada1d-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ada1d-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="ada1d-122">Especifica os parâmetros para um token de segurança emitido em um cenário de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="ada1d-122">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ada1d-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="ada1d-123">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ada1d-124">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="ada1d-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ada1d-125">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="ada1d-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ada1d-126">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="ada1d-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="ada1d-127">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="ada1d-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ada1d-128">Associações</span><span class="sxs-lookup"><span data-stu-id="ada1d-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ada1d-129">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="ada1d-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ada1d-130">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="ada1d-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="ada1d-131">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ada1d-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="ada1d-132">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="ada1d-132">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
