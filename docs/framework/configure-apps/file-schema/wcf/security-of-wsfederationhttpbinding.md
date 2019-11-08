---
title: <security> de <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: ea029444cee331a235c7a2fc140b4321d7530063
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736320"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="c6dfe-102">\<> de segurança do \<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c6dfe-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="c6dfe-103">Define as configurações de segurança do [\<WSFederationHttpBinding](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c6dfe-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="c6dfe-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c6dfe-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c6dfe-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="c6dfe-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c6dfe-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="c6dfe-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c6dfe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c6dfe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="c6dfe-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="c6dfe-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="c6dfe-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**security >**</span><span class="sxs-lookup"><span data-stu-id="c6dfe-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6dfe-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6dfe-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6dfe-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c6dfe-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c6dfe-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6dfe-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="c6dfe-113">Attributes</span></span>  
  
|<span data-ttu-id="c6dfe-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="c6dfe-114">Attribute</span></span>|<span data-ttu-id="c6dfe-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6dfe-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6dfe-116">Modo</span><span class="sxs-lookup"><span data-stu-id="c6dfe-116">Mode</span></span>|<span data-ttu-id="c6dfe-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-117">Optional.</span></span> <span data-ttu-id="c6dfe-118">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="c6dfe-119">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-119">The default value is `Message`.</span></span> <span data-ttu-id="c6dfe-120">Este atributo é do tipo <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-120">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="c6dfe-121">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="c6dfe-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="c6dfe-122">Valor</span><span class="sxs-lookup"><span data-stu-id="c6dfe-122">Value</span></span>|<span data-ttu-id="c6dfe-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6dfe-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c6dfe-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c6dfe-124">None</span></span>|<span data-ttu-id="c6dfe-125">A mensagem SOAP não é segura durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-125">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="c6dfe-126">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c6dfe-126">Message</span></span>|<span data-ttu-id="c6dfe-127">São fornecidos os serviços de integridade, confidencialidade, autenticação de servidor e autenticação de cliente usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-127">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="c6dfe-128">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="c6dfe-129">O serviço precisa ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-129">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="c6dfe-130">A autenticação de cliente é baseada no token emitido para o cliente por um serviço de token de segurança</span><span class="sxs-lookup"><span data-stu-id="c6dfe-130">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="c6dfe-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="c6dfe-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="c6dfe-132">A integridade, a confidencialidade e a autenticação de servidor são fornecidas por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-132">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="c6dfe-133">O serviço precisa ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-133">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="c6dfe-134">A autenticação de cliente é fornecida por meio de segurança de mensagens SOAP e é baseada no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-134">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6dfe-135">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c6dfe-135">Child Elements</span></span>  
  
|<span data-ttu-id="c6dfe-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6dfe-136">Element</span></span>|<span data-ttu-id="c6dfe-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6dfe-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6dfe-138">\<message ></span><span class="sxs-lookup"><span data-stu-id="c6dfe-138">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="c6dfe-139">Define as configurações para a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-139">Defines the settings for the message-level security.</span></span> <span data-ttu-id="c6dfe-140">Este elemento é do tipo <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-140">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6dfe-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c6dfe-141">Parent Elements</span></span>  
  
|<span data-ttu-id="c6dfe-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6dfe-142">Element</span></span>|<span data-ttu-id="c6dfe-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6dfe-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6dfe-144">\<binding ></span><span class="sxs-lookup"><span data-stu-id="c6dfe-144">\<binding></span></span>](bindings.md)|<span data-ttu-id="c6dfe-145">Define todos os recursos de associação do [\<wsDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c6dfe-145">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6dfe-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6dfe-146">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="c6dfe-147">Como criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c6dfe-147">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="c6dfe-148">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c6dfe-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c6dfe-149">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="c6dfe-149">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="c6dfe-150">Associações</span><span class="sxs-lookup"><span data-stu-id="c6dfe-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c6dfe-151">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c6dfe-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c6dfe-152">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c6dfe-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c6dfe-153">\<binding ></span><span class="sxs-lookup"><span data-stu-id="c6dfe-153">\<binding></span></span>](bindings.md)
