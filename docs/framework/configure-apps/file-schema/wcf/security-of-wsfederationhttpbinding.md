---
title: <security> De <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 5316060d4122a443dd0223ce1ee9cdd39efac0b8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282055"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="94c0a-102">\<segurança > de \<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="94c0a-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="94c0a-103">Define as configurações de segurança de [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="94c0a-103">Defines the security settings of the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="94c0a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="94c0a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="94c0a-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="94c0a-105">\<bindings></span></span>  
<span data-ttu-id="94c0a-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="94c0a-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="94c0a-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="94c0a-107">\<binding></span></span>  
<span data-ttu-id="94c0a-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="94c0a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94c0a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94c0a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94c0a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="94c0a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="94c0a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="94c0a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94c0a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="94c0a-112">Attributes</span></span>  
  
|<span data-ttu-id="94c0a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="94c0a-113">Attribute</span></span>|<span data-ttu-id="94c0a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="94c0a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94c0a-115">Modo</span><span class="sxs-lookup"><span data-stu-id="94c0a-115">Mode</span></span>|<span data-ttu-id="94c0a-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c0a-116">Optional.</span></span> <span data-ttu-id="94c0a-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="94c0a-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="94c0a-118">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="94c0a-118">The default value is `Message`.</span></span> <span data-ttu-id="94c0a-119">Esse atributo é do tipo <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="94c0a-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="94c0a-120">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="94c0a-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="94c0a-121">Valor</span><span class="sxs-lookup"><span data-stu-id="94c0a-121">Value</span></span>|<span data-ttu-id="94c0a-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="94c0a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="94c0a-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="94c0a-123">None</span></span>|<span data-ttu-id="94c0a-124">A mensagem SOAP não é segura durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="94c0a-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="94c0a-125">Mensagem</span><span class="sxs-lookup"><span data-stu-id="94c0a-125">Message</span></span>|<span data-ttu-id="94c0a-126">São fornecidos os serviços de integridade, confidencialidade, autenticação de servidor e autenticação de cliente usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="94c0a-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="94c0a-127">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="94c0a-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="94c0a-128">O serviço precisa ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="94c0a-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="94c0a-129">Autenticação de cliente baseia-se no token emitido ao cliente por um serviço de token de segurança</span><span class="sxs-lookup"><span data-stu-id="94c0a-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="94c0a-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="94c0a-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="94c0a-131">A integridade, a confidencialidade e a autenticação de servidor são fornecidas por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="94c0a-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="94c0a-132">O serviço precisa ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="94c0a-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="94c0a-133">A autenticação de cliente é fornecida por meio de segurança de mensagens SOAP e é baseada no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="94c0a-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94c0a-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="94c0a-134">Child Elements</span></span>  
  
|<span data-ttu-id="94c0a-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="94c0a-135">Element</span></span>|<span data-ttu-id="94c0a-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="94c0a-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94c0a-137">\<message></span><span class="sxs-lookup"><span data-stu-id="94c0a-137">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="94c0a-138">Define as configurações para a segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="94c0a-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="94c0a-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="94c0a-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94c0a-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="94c0a-140">Parent Elements</span></span>  
  
|<span data-ttu-id="94c0a-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="94c0a-141">Element</span></span>|<span data-ttu-id="94c0a-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="94c0a-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94c0a-143">\<binding></span><span class="sxs-lookup"><span data-stu-id="94c0a-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="94c0a-144">Define todos os recursos de associação do [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="94c0a-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94c0a-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94c0a-145">See also</span></span>
- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="94c0a-146">Como: Criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="94c0a-146">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="94c0a-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="94c0a-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="94c0a-148">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="94c0a-148">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="94c0a-149">Associações</span><span class="sxs-lookup"><span data-stu-id="94c0a-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="94c0a-150">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="94c0a-150">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="94c0a-151">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="94c0a-151">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="94c0a-152">\<binding></span><span class="sxs-lookup"><span data-stu-id="94c0a-152">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
