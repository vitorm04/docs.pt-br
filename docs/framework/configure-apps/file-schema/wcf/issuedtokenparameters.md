---
title: '&lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ef68585054d61de8c25b7e3effd1d72063d4589c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuedtokenparametersgt"></a><span data-ttu-id="fab0b-102">&lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="fab0b-102">&lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="fab0b-103">Especifica os parâmetros para um token de segurança emitido em um cenário de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="fab0b-103">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="fab0b-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fab0b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fab0b-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="fab0b-105">\<bindings></span></span>  
<span data-ttu-id="fab0b-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fab0b-106">\<customBinding></span></span>  
<span data-ttu-id="fab0b-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="fab0b-107">\<binding></span></span>  
<span data-ttu-id="fab0b-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="fab0b-108">\<security></span></span>  
<span data-ttu-id="fab0b-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="fab0b-109">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fab0b-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fab0b-110">Syntax</span></span>  
  
```xml  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## <a name="type"></a><span data-ttu-id="fab0b-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="fab0b-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fab0b-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fab0b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fab0b-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fab0b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fab0b-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="fab0b-114">Attributes</span></span>  
  
|<span data-ttu-id="fab0b-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="fab0b-115">Attribute</span></span>|<span data-ttu-id="fab0b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="fab0b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fab0b-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="fab0b-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="fab0b-118">Especifica as versões das especificações de segurança, (WS-Security, WS-Trust, WS-Secure Conversation e WS-Security Policy) que devem ser suportadas pela associação.</span><span class="sxs-lookup"><span data-stu-id="fab0b-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="fab0b-119">Esse valor é do tipo <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="fab0b-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="fab0b-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="fab0b-120">inclusionMode</span></span>|<span data-ttu-id="fab0b-121">Especifica os requisitos de inclusão de token.</span><span class="sxs-lookup"><span data-stu-id="fab0b-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="fab0b-122">Esse atributo é do tipo <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="fab0b-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="fab0b-123">Tamanho da chave</span><span class="sxs-lookup"><span data-stu-id="fab0b-123">keySize</span></span>|<span data-ttu-id="fab0b-124">Um inteiro que especifica o tamanho de chave de token.</span><span class="sxs-lookup"><span data-stu-id="fab0b-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="fab0b-125">O valor padrão é 256.</span><span class="sxs-lookup"><span data-stu-id="fab0b-125">The default value is 256.</span></span>|  
|<span data-ttu-id="fab0b-126">KeyType</span><span class="sxs-lookup"><span data-stu-id="fab0b-126">keyType</span></span>|<span data-ttu-id="fab0b-127">Um valor válido de <xref:System.IdentityModel.Tokens.SecurityKeyType> que especifica o tipo de chave.</span><span class="sxs-lookup"><span data-stu-id="fab0b-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="fab0b-128">O padrão é `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="fab0b-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="fab0b-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="fab0b-129">tokenType</span></span>|<span data-ttu-id="fab0b-130">Uma cadeia de caracteres que especifica o tipo de token.</span><span class="sxs-lookup"><span data-stu-id="fab0b-130">A string that specifies the token type.</span></span> <span data-ttu-id="fab0b-131">O padrão é "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="fab0b-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fab0b-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fab0b-132">Child Elements</span></span>  
  
|<span data-ttu-id="fab0b-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="fab0b-133">Element</span></span>|<span data-ttu-id="fab0b-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="fab0b-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fab0b-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="fab0b-135">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="fab0b-136">Uma coleção de elementos de configuração que especificam parâmetros de solicitação adicionais.</span><span class="sxs-lookup"><span data-stu-id="fab0b-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="fab0b-137">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="fab0b-137">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="fab0b-138">Especifica uma coleção de tipos de declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="fab0b-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="fab0b-139">Em um cenário federado, serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="fab0b-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="fab0b-140">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="fab0b-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="fab0b-141">Cada elemento na coleção Especifica os tipos de declarações obrigatórias e opcionais que deve aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="fab0b-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="fab0b-142">\<emissor ></span><span class="sxs-lookup"><span data-stu-id="fab0b-142">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="fab0b-143">Um elemento de configuração que especifica o ponto de extremidade que emite o token atual.</span><span class="sxs-lookup"><span data-stu-id="fab0b-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="fab0b-144">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="fab0b-144">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="fab0b-145">Um elemento de configuração que especifica o endereço do ponto de extremidade de metadados do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="fab0b-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fab0b-146">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fab0b-146">Parent Elements</span></span>  
  
|<span data-ttu-id="fab0b-147">Elemento</span><span class="sxs-lookup"><span data-stu-id="fab0b-147">Element</span></span>|<span data-ttu-id="fab0b-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="fab0b-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fab0b-149">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="fab0b-149">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="fab0b-150">Especifica os valores padrão usados para iniciar um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="fab0b-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="fab0b-151">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="fab0b-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="fab0b-152">Especifica as opções de segurança para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="fab0b-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fab0b-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fab0b-153">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <span data-ttu-id="fab0b-154">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="fab0b-154">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="fab0b-155">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="fab0b-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="fab0b-156">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="fab0b-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="fab0b-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fab0b-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="fab0b-158">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="fab0b-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="fab0b-159">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="fab0b-159">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [<span data-ttu-id="fab0b-160">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="fab0b-160">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="fab0b-161">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="fab0b-161">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="fab0b-162">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="fab0b-162">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="fab0b-163">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="fab0b-163">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
