---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 6bdf56e3d2084dec8d44e1c4d3f0c1e50b711b92
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758231"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="36d18-101">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="36d18-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="36d18-102">Especifica os parâmetros para um token de segurança emitido em um cenário de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="36d18-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="36d18-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="36d18-103">\<system.serviceModel></span></span>  
<span data-ttu-id="36d18-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="36d18-104">\<bindings></span></span>  
<span data-ttu-id="36d18-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="36d18-105">\<customBinding></span></span>  
<span data-ttu-id="36d18-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="36d18-106">\<binding></span></span>  
<span data-ttu-id="36d18-107">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="36d18-107">\<security></span></span>  
<span data-ttu-id="36d18-108">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="36d18-108">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36d18-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36d18-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="36d18-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="36d18-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36d18-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="36d18-111">Attributes and Elements</span></span>  
 <span data-ttu-id="36d18-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="36d18-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36d18-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="36d18-113">Attributes</span></span>  
  
|<span data-ttu-id="36d18-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="36d18-114">Attribute</span></span>|<span data-ttu-id="36d18-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="36d18-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36d18-116">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="36d18-116">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="36d18-117">Especifica as versões das especificações de segurança, (WS-Security, WS-Trust, WS-Secure Conversation e WS-Security Policy) que devem ser suportadas pela associação.</span><span class="sxs-lookup"><span data-stu-id="36d18-117">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="36d18-118">Esse valor é do tipo <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="36d18-118">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="36d18-119">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="36d18-119">inclusionMode</span></span>|<span data-ttu-id="36d18-120">Especifica os requisitos de inclusão de token.</span><span class="sxs-lookup"><span data-stu-id="36d18-120">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="36d18-121">Esse atributo é do tipo <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="36d18-121">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="36d18-122">keySize</span><span class="sxs-lookup"><span data-stu-id="36d18-122">keySize</span></span>|<span data-ttu-id="36d18-123">Um inteiro que especifica o tamanho de chave de token.</span><span class="sxs-lookup"><span data-stu-id="36d18-123">An integer that specifies the token key size.</span></span> <span data-ttu-id="36d18-124">O valor padrão é 256.</span><span class="sxs-lookup"><span data-stu-id="36d18-124">The default value is 256.</span></span>|  
|<span data-ttu-id="36d18-125">keyType</span><span class="sxs-lookup"><span data-stu-id="36d18-125">keyType</span></span>|<span data-ttu-id="36d18-126">Um valor válido de <xref:System.IdentityModel.Tokens.SecurityKeyType> que especifica o tipo de chave.</span><span class="sxs-lookup"><span data-stu-id="36d18-126">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="36d18-127">O padrão é `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="36d18-127">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="36d18-128">tokenType</span><span class="sxs-lookup"><span data-stu-id="36d18-128">tokenType</span></span>|<span data-ttu-id="36d18-129">Uma cadeia de caracteres que especifica o tipo de token.</span><span class="sxs-lookup"><span data-stu-id="36d18-129">A string that specifies the token type.</span></span> <span data-ttu-id="36d18-130">O padrão é "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="36d18-130">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36d18-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="36d18-131">Child Elements</span></span>  
  
|<span data-ttu-id="36d18-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="36d18-132">Element</span></span>|<span data-ttu-id="36d18-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="36d18-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36d18-134">\<additionalRequestParameters></span><span class="sxs-lookup"><span data-stu-id="36d18-134">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="36d18-135">Uma coleção de elementos de configuração que especificam parâmetros de solicitação adicionais.</span><span class="sxs-lookup"><span data-stu-id="36d18-135">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="36d18-136">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="36d18-136">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="36d18-137">Especifica uma coleção de tipos de declaração exigidos.</span><span class="sxs-lookup"><span data-stu-id="36d18-137">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="36d18-138">Em um cenário federado, os serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="36d18-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="36d18-139">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="36d18-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="36d18-140">Cada elemento nesta coleção Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="36d18-140">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="36d18-141">\<issuer></span><span class="sxs-lookup"><span data-stu-id="36d18-141">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="36d18-142">Um elemento de configuração que especifica o ponto de extremidade que emite o token atual.</span><span class="sxs-lookup"><span data-stu-id="36d18-142">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="36d18-143">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="36d18-143">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="36d18-144">Um elemento de configuração que especifica o endereço do ponto de extremidade de metadados do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="36d18-144">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36d18-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="36d18-145">Parent Elements</span></span>  
  
|<span data-ttu-id="36d18-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="36d18-146">Element</span></span>|<span data-ttu-id="36d18-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="36d18-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36d18-148">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="36d18-148">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="36d18-149">Especifica os valores padrão usados para iniciar um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="36d18-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="36d18-150">\<security></span><span class="sxs-lookup"><span data-stu-id="36d18-150">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="36d18-151">Especifica as opções de segurança para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="36d18-151">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36d18-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36d18-152">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="36d18-153">Associações</span><span class="sxs-lookup"><span data-stu-id="36d18-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="36d18-154">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="36d18-154">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="36d18-155">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="36d18-155">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="36d18-156">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="36d18-156">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="36d18-157">Como: Criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="36d18-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="36d18-158">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="36d18-158">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="36d18-159">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="36d18-159">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="36d18-160">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="36d18-160">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="36d18-161">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="36d18-161">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="36d18-162">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="36d18-162">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
