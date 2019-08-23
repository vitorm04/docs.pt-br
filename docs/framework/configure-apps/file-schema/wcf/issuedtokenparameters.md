---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 07fc2c4c52c29de1cfc9f498a6dc6b6da887b502
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925339"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="787e8-101">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="787e8-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="787e8-102">Especifica os parâmetros para um token de segurança emitido em um cenário de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="787e8-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="787e8-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="787e8-103">\<system.serviceModel></span></span>  
<span data-ttu-id="787e8-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="787e8-104">\<bindings></span></span>  
<span data-ttu-id="787e8-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="787e8-105">\<customBinding></span></span>  
<span data-ttu-id="787e8-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="787e8-106">\<binding></span></span>  
<span data-ttu-id="787e8-107">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="787e8-107">\<security></span></span>  
<span data-ttu-id="787e8-108">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="787e8-108">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="787e8-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="787e8-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="787e8-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="787e8-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="787e8-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="787e8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="787e8-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="787e8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="787e8-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="787e8-113">Attributes</span></span>  
  
|<span data-ttu-id="787e8-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="787e8-114">Attribute</span></span>|<span data-ttu-id="787e8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="787e8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="787e8-116">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="787e8-116">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="787e8-117">Especifica as versões das especificações de segurança, (WS-Security, WS-Trust, WS-Secure Conversation e WS-Security Policy) que devem ser suportadas pela associação.</span><span class="sxs-lookup"><span data-stu-id="787e8-117">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="787e8-118">Esse valor é do tipo <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="787e8-118">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="787e8-119">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="787e8-119">inclusionMode</span></span>|<span data-ttu-id="787e8-120">Especifica os requisitos de inclusão de token.</span><span class="sxs-lookup"><span data-stu-id="787e8-120">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="787e8-121">Esse atributo é do tipo <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="787e8-121">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="787e8-122">keySize</span><span class="sxs-lookup"><span data-stu-id="787e8-122">keySize</span></span>|<span data-ttu-id="787e8-123">Um inteiro que especifica o tamanho da chave do token.</span><span class="sxs-lookup"><span data-stu-id="787e8-123">An integer that specifies the token key size.</span></span> <span data-ttu-id="787e8-124">O valor padrão é 256.</span><span class="sxs-lookup"><span data-stu-id="787e8-124">The default value is 256.</span></span>|  
|<span data-ttu-id="787e8-125">keyType</span><span class="sxs-lookup"><span data-stu-id="787e8-125">keyType</span></span>|<span data-ttu-id="787e8-126">Um valor válido de <xref:System.IdentityModel.Tokens.SecurityKeyType> que especifica o tipo de chave.</span><span class="sxs-lookup"><span data-stu-id="787e8-126">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="787e8-127">O padrão é `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="787e8-127">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="787e8-128">tokenType</span><span class="sxs-lookup"><span data-stu-id="787e8-128">tokenType</span></span>|<span data-ttu-id="787e8-129">Uma cadeia de caracteres que especifica o tipo de token.</span><span class="sxs-lookup"><span data-stu-id="787e8-129">A string that specifies the token type.</span></span> <span data-ttu-id="787e8-130">O padrão é "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="787e8-130">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="787e8-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="787e8-131">Child Elements</span></span>  
  
|<span data-ttu-id="787e8-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="787e8-132">Element</span></span>|<span data-ttu-id="787e8-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="787e8-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="787e8-134">\<additionalRequestParameters></span><span class="sxs-lookup"><span data-stu-id="787e8-134">\<additionalRequestParameters></span></span>](additionalrequestparameters-element.md)|<span data-ttu-id="787e8-135">Uma coleção de elementos de configuração que especificam parâmetros de solicitação adicionais.</span><span class="sxs-lookup"><span data-stu-id="787e8-135">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="787e8-136">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="787e8-136">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="787e8-137">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="787e8-137">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="787e8-138">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="787e8-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="787e8-139">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="787e8-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="787e8-140">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="787e8-140">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="787e8-141">\<issuer></span><span class="sxs-lookup"><span data-stu-id="787e8-141">\<issuer></span></span>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="787e8-142">Um elemento de configuração que especifica o ponto de extremidade que emite o token atual.</span><span class="sxs-lookup"><span data-stu-id="787e8-142">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="787e8-143">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="787e8-143">\<issuerMetadata></span></span>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="787e8-144">Um elemento de configuração que especifica o endereço do ponto de extremidade dos metadados do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="787e8-144">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="787e8-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="787e8-145">Parent Elements</span></span>  
  
|<span data-ttu-id="787e8-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="787e8-146">Element</span></span>|<span data-ttu-id="787e8-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="787e8-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="787e8-148">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="787e8-148">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="787e8-149">Especifica os valores padrão usados para iniciar um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="787e8-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="787e8-150">\<security></span><span class="sxs-lookup"><span data-stu-id="787e8-150">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="787e8-151">Especifica as opções de segurança para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="787e8-151">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="787e8-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="787e8-152">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="787e8-153">Associações</span><span class="sxs-lookup"><span data-stu-id="787e8-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="787e8-154">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="787e8-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="787e8-155">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="787e8-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="787e8-156">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="787e8-156">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="787e8-157">Como: Criar uma associação personalizada usando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="787e8-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="787e8-158">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="787e8-158">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="787e8-159">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="787e8-159">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="787e8-160">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="787e8-160">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="787e8-161">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="787e8-161">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="787e8-162">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="787e8-162">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
