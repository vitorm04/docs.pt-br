---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: c90024a0629f39d160967ca00434e48f682d8933
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157311"
---
# \<issuedTokenParameters>

<span data-ttu-id="845f2-101">Especifica os parâmetros para um token de segurança emitido em um cenário de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="845f2-101">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="845f2-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="845f2-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="845f2-103">Tipo</span><span class="sxs-lookup"><span data-stu-id="845f2-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="845f2-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="845f2-104">Attributes and Elements</span></span>  

 <span data-ttu-id="845f2-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="845f2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="845f2-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="845f2-106">Attributes</span></span>  
  
|<span data-ttu-id="845f2-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="845f2-107">Attribute</span></span>|<span data-ttu-id="845f2-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="845f2-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="845f2-109">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="845f2-109">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="845f2-110">Especifica as versões das especificações de segurança, (WS-Security, WS-Trust, WS-Secure Conversation e WS-Security Policy) que devem ser suportadas pela associação.</span><span class="sxs-lookup"><span data-stu-id="845f2-110">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="845f2-111">Esse valor é do tipo <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="845f2-111">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="845f2-112">inclusõesmode</span><span class="sxs-lookup"><span data-stu-id="845f2-112">inclusionMode</span></span>|<span data-ttu-id="845f2-113">Especifica os requisitos de inclusão de token.</span><span class="sxs-lookup"><span data-stu-id="845f2-113">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="845f2-114">Esse atributo é do tipo <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> .</span><span class="sxs-lookup"><span data-stu-id="845f2-114">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="845f2-115">keySize</span><span class="sxs-lookup"><span data-stu-id="845f2-115">keySize</span></span>|<span data-ttu-id="845f2-116">Um inteiro que especifica o tamanho da chave do token.</span><span class="sxs-lookup"><span data-stu-id="845f2-116">An integer that specifies the token key size.</span></span> <span data-ttu-id="845f2-117">O valor padrão é 256.</span><span class="sxs-lookup"><span data-stu-id="845f2-117">The default value is 256.</span></span>|  
|<span data-ttu-id="845f2-118">keyType</span><span class="sxs-lookup"><span data-stu-id="845f2-118">keyType</span></span>|<span data-ttu-id="845f2-119">Um valor válido de <xref:System.IdentityModel.Tokens.SecurityKeyType> que especifica o tipo de chave.</span><span class="sxs-lookup"><span data-stu-id="845f2-119">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="845f2-120">O padrão é `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="845f2-120">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="845f2-121">tokenType</span><span class="sxs-lookup"><span data-stu-id="845f2-121">tokenType</span></span>|<span data-ttu-id="845f2-122">Uma cadeia de caracteres que especifica o tipo de token.</span><span class="sxs-lookup"><span data-stu-id="845f2-122">A string that specifies the token type.</span></span> <span data-ttu-id="845f2-123">O padrão é "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="845f2-123">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="845f2-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="845f2-124">Child Elements</span></span>  
  
|<span data-ttu-id="845f2-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="845f2-125">Element</span></span>|<span data-ttu-id="845f2-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="845f2-126">Description</span></span>|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|<span data-ttu-id="845f2-127">Uma coleção de elementos de configuração que especificam parâmetros de solicitação adicionais.</span><span class="sxs-lookup"><span data-stu-id="845f2-127">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="845f2-128">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="845f2-128">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="845f2-129">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="845f2-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="845f2-130">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="845f2-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="845f2-131">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="845f2-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="845f2-132">Um elemento de configuração que especifica o ponto de extremidade que emite o token atual.</span><span class="sxs-lookup"><span data-stu-id="845f2-132">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="845f2-133">Um elemento de configuração que especifica o endereço do ponto de extremidade dos metadados do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="845f2-133">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="845f2-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="845f2-134">Parent Elements</span></span>  
  
|<span data-ttu-id="845f2-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="845f2-135">Element</span></span>|<span data-ttu-id="845f2-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="845f2-136">Description</span></span>|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="845f2-137">Especifica os valores padrão usados para iniciar um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="845f2-137">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="845f2-138">Especifica as opções de segurança para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="845f2-138">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="845f2-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="845f2-139">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="845f2-140">Associações</span><span class="sxs-lookup"><span data-stu-id="845f2-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="845f2-141">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="845f2-141">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="845f2-142">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="845f2-142">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="845f2-143">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="845f2-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="845f2-144">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="845f2-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="845f2-145">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="845f2-145">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="845f2-146">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="845f2-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="845f2-147">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="845f2-147">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="845f2-148">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="845f2-148">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
