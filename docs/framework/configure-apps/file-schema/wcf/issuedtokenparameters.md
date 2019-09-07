---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 8432463ff62e4b5e54a491b574cc6a5285efe220
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397951"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="02af1-101">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="02af1-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="02af1-102">Especifica os parâmetros para um token de segurança emitido em um cenário de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="02af1-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
<span data-ttu-id="02af1-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="02af1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="02af1-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="02af1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="02af1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="02af1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="02af1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="02af1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="02af1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="02af1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="02af1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="02af1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="02af1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> issuedTokenParameters**</span><span class="sxs-lookup"><span data-stu-id="02af1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02af1-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02af1-110">Syntax</span></span>  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a><span data-ttu-id="02af1-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="02af1-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02af1-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="02af1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="02af1-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="02af1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02af1-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="02af1-114">Attributes</span></span>  
  
|<span data-ttu-id="02af1-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="02af1-115">Attribute</span></span>|<span data-ttu-id="02af1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="02af1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02af1-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="02af1-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="02af1-118">Especifica as versões das especificações de segurança, (WS-Security, WS-Trust, WS-Secure Conversation e WS-Security Policy) que devem ser suportadas pela associação.</span><span class="sxs-lookup"><span data-stu-id="02af1-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="02af1-119">Esse valor é do tipo <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="02af1-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="02af1-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="02af1-120">inclusionMode</span></span>|<span data-ttu-id="02af1-121">Especifica os requisitos de inclusão de token.</span><span class="sxs-lookup"><span data-stu-id="02af1-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="02af1-122">Esse atributo é do tipo <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="02af1-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="02af1-123">keySize</span><span class="sxs-lookup"><span data-stu-id="02af1-123">keySize</span></span>|<span data-ttu-id="02af1-124">Um inteiro que especifica o tamanho da chave do token.</span><span class="sxs-lookup"><span data-stu-id="02af1-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="02af1-125">O valor padrão é 256.</span><span class="sxs-lookup"><span data-stu-id="02af1-125">The default value is 256.</span></span>|  
|<span data-ttu-id="02af1-126">keyType</span><span class="sxs-lookup"><span data-stu-id="02af1-126">keyType</span></span>|<span data-ttu-id="02af1-127">Um valor válido de <xref:System.IdentityModel.Tokens.SecurityKeyType> que especifica o tipo de chave.</span><span class="sxs-lookup"><span data-stu-id="02af1-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="02af1-128">O padrão é `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="02af1-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="02af1-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="02af1-129">tokenType</span></span>|<span data-ttu-id="02af1-130">Uma cadeia de caracteres que especifica o tipo de token.</span><span class="sxs-lookup"><span data-stu-id="02af1-130">A string that specifies the token type.</span></span> <span data-ttu-id="02af1-131">O padrão é "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="02af1-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02af1-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="02af1-132">Child Elements</span></span>  
  
|<span data-ttu-id="02af1-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="02af1-133">Element</span></span>|<span data-ttu-id="02af1-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="02af1-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02af1-135">\<additionalRequestParameters></span><span class="sxs-lookup"><span data-stu-id="02af1-135">\<additionalRequestParameters></span></span>](additionalrequestparameters-element.md)|<span data-ttu-id="02af1-136">Uma coleção de elementos de configuração que especificam parâmetros de solicitação adicionais.</span><span class="sxs-lookup"><span data-stu-id="02af1-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="02af1-137">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="02af1-137">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="02af1-138">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="02af1-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="02af1-139">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="02af1-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="02af1-140">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="02af1-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="02af1-141">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="02af1-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="02af1-142">\<issuer></span><span class="sxs-lookup"><span data-stu-id="02af1-142">\<issuer></span></span>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="02af1-143">Um elemento de configuração que especifica o ponto de extremidade que emite o token atual.</span><span class="sxs-lookup"><span data-stu-id="02af1-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="02af1-144">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="02af1-144">\<issuerMetadata></span></span>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="02af1-145">Um elemento de configuração que especifica o endereço do ponto de extremidade dos metadados do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="02af1-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02af1-146">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="02af1-146">Parent Elements</span></span>  
  
|<span data-ttu-id="02af1-147">Elemento</span><span class="sxs-lookup"><span data-stu-id="02af1-147">Element</span></span>|<span data-ttu-id="02af1-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="02af1-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02af1-149">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="02af1-149">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="02af1-150">Especifica os valores padrão usados para iniciar um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="02af1-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="02af1-151">\<security></span><span class="sxs-lookup"><span data-stu-id="02af1-151">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="02af1-152">Especifica as opções de segurança para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="02af1-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02af1-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02af1-153">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="02af1-154">Associações</span><span class="sxs-lookup"><span data-stu-id="02af1-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="02af1-155">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="02af1-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="02af1-156">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="02af1-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="02af1-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="02af1-157">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="02af1-158">Como: Criar uma associação personalizada usando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="02af1-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="02af1-159">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="02af1-159">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="02af1-160">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="02af1-160">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="02af1-161">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="02af1-161">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="02af1-162">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="02af1-162">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="02af1-163">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="02af1-163">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
